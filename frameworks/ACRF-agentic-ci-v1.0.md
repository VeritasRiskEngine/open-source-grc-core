#!/usr/bin/env python3
"""
open-source-grc-core (VeritasRiskEngine)
Quantitative Risk Calculation Engine: engine/risk_calculator.py

Calculates dynamic residual risk for Agentic AI and Multi-Domain Critical Infrastructure
incorporating Edge-Node Health Drift (D) and Temporal Risk Horizons (T_temp).

Formula:
    Residual Risk (R) = (Inherent Impact [I] * Likelihood [L]) * Edge Drift Factor [D] * Temporal Risk Factor [T]
"""

from dataclasses import dataclass, asdict
from enum import Enum
import argparse
import json
import math
import sys
from typing import Dict, Any


class RiskTier(Enum):
    LOW = "LOW"
    MODERATE = "MODERATE"
    HIGH = "HIGH"
    CRITICAL = "CRITICAL"


@dataclass
class RiskInput:
    impact: float       # Scale 1.0 to 5.0
    likelihood: float   # Scale 1.0 to 5.0
    edge_drift: float   # Multiplier >= 1.0 (Baseline = 1.0)
    system_life_years: float = 5.0      # Data/System protection lifespan
    adversary_break_years: float = 10.0 # Time for adversary to break crypto/scaffolding


@dataclass
class RiskOutput:
    base_inherent_risk: float
    adjusted_residual_risk: float
    temporal_risk_factor: float
    risk_tier: RiskTier
    action_required: str

    def to_dict(self) -> Dict[str, Any]:
        data = asdict(self)
        data['risk_tier'] = self.risk_tier.value
        return data


class ACRFRiskEngine:
    """
    Advanced Convergence Resilience Framework (ACRF v1.0) Quantitative Scoring Engine.
    """

    SCORE_THRESHOLDS = {
        RiskTier.LOW: 12.0,
        RiskTier.MODERATE: 25.0,
        RiskTier.HIGH: 50.0,
        # Scores above 50.0 are categorized as CRITICAL
    }

    ACTION_MAP = {
        RiskTier.LOW: "Standard Onboarding / Routine Telemetry Logging",
        RiskTier.MODERATE: "Mandatory Daily Red-Team Testing & Enhanced Telemetry Monitoring",
        RiskTier.HIGH: "Tier 1-2 Soft Kill Switch Enforcement & Runtime Autonomy Throttling",
        RiskTier.CRITICAL: "Tier 3-5 Out-of-Band Physical Isolation & Immediate Incident Response",
    }

    def __init__(self, input_data: RiskInput):
        self._validate_inputs(input_data)
        self.input = input_data

    @staticmethod
    def _validate_inputs(data: RiskInput) -> None:
        if not (1.0 <= data.impact <= 5.0):
            raise ValueError(f"Impact must be between 1.0 and 5.0. Got: {data.impact}")
        if not (1.0 <= data.likelihood <= 5.0):
            raise ValueError(f"Likelihood must be between 1.0 and 5.0. Got: {data.likelihood}")
        if data.edge_drift < 1.0:
            raise ValueError(f"Edge Drift Factor (D) must be >= 1.0. Got: {data.edge_drift}")
        if data.system_life_years <= 0 or data.adversary_break_years <= 0:
            raise ValueError("Temporal parameters must be strictly positive values.")

    def calculate_temporal_factor(self) -> float:
        """
        Calculates temporal risk factor based on quantum/capability break timelines.
        Formula: max(1.0, 1 + ln(T_system_life / T_adversary_break)) if life > break else 1.0
        """
        if self.input.system_life_years > self.input.adversary_break_years:
            delta = self.input.system_life_years / self.input.adversary_break_years
            return round(1.0 + math.log(delta), 3)
        return 1.0

    def calculate(self) -> RiskOutput:
        base_inherent = self.input.impact * self.input.likelihood
        temporal_factor = self.calculate_temporal_factor()
        adjusted_risk = round(base_inherent * self.input.edge_drift * temporal_factor, 2)

        if adjusted_risk <= self.SCORE_THRESHOLDS[RiskTier.LOW]:
            tier = RiskTier.LOW
        elif adjusted_risk <= self.SCORE_THRESHOLDS[RiskTier.MODERATE]:
            tier = RiskTier.MODERATE
        elif adjusted_risk <= self.SCORE_THRESHOLDS[RiskTier.HIGH]:
            tier = RiskTier.HIGH
        else:
            tier = RiskTier.CRITICAL

        return RiskOutput(
            base_inherent_risk=round(base_inherent, 2),
            adjusted_residual_risk=adjusted_risk,
            temporal_risk_factor=temporal_factor,
            risk_tier=tier,
            action_required=self.ACTION_MAP[tier]
        )


def main():
    parser = argparse.ArgumentParser(
        description="VeritasRiskEngine - Quantitative Risk Engine (ACRF v1.0)",
        formatter_class=argparse.ArgumentDefaultsHelpFormatter
    )
    parser.add_argument("-i", "--impact", type=float, required=True, help="Inherent Impact (1.0 - 5.0)")
    parser.add_argument("-l", "--likelihood", type=float, required=True, help="Inherent Likelihood (1.0 - 5.0)")
    parser.add_argument("-d", "--drift", type=float, default=1.0, help="Edge Node Drift Factor (>= 1.0)")
    parser.add_argument("--sys-life", type=float, default=5.0, help="System/Data Protection Lifespan (Years)")
    parser.add_argument("--adv-break", type=float, default=10.0, help="Adversary Capability Break Time (Years)")
    parser.add_argument("--json", action="store_true", help="Output results in JSON format")

    args = parser.parse_args()

    try:
        risk_input = RiskInput(
            impact=args.impact,
            likelihood=args.likelihood,
            edge_drift=args.drift,
            system_life_years=args.sys_life,
            adversary_break_years=args.adv_break
        )
        engine = ACRFRiskEngine(risk_input)
        result = engine.calculate()

        if args.json:
            print(json.dumps(result.to_dict(), indent=2))
        else:
            color_code = {
                RiskTier.LOW: "\033[92m",      # Green
                RiskTier.MODERATE: "\033[93m", # Yellow
                RiskTier.HIGH: "\033[91m",     # Red
                RiskTier.CRITICAL: "\033[95m"  # Magenta
            }.get(result.risk_tier, "\033[0m")
            reset = "\033[0m"

            print("\n" + "=" * 55)
            print(" VERITAS RISK ENGINE - QUANTITATIVE EVALUATION")
            print("=" * 55)
            print(f" Inherent Risk (I x L)    : {result.base_inherent_risk}")
            print(f" Edge Drift Factor (D)   : {args.drift}")
            print(f" Temporal Risk Factor (T): {result.temporal_risk_factor}")
            print(f" Adjusted Residual Risk  : {result.adjusted_residual_risk}")
            print(f" Risk Tier               : {color_code}{result.risk_tier.value}{reset}")
            print(f" Action Required         : {result.action_required}")
            print("=" * 55 + "\n")

    except ValueError as e:
        print(f"Configuration Error: {e}", file=sys.stderr)
        sys.exit(1)


if __name__ == "__main__":
    main()
