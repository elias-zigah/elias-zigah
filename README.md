# Elias Zigah

**Machine learning researcher — reinforcement learning for autonomous mobility.**
CentraleSupélec, Université Paris-Saclay · EU ULTIMO project · Paris, France

I build simulation environments and constrained reinforcement learning methods for shared
autonomous vehicle services, and I design the evaluation protocols that decide whether the
resulting policies can be trusted. My background is in transport and energy economics, which
shapes the problems I work on: pricing, fleet sizing, and the trade-off between operator
viability and passenger access under regulatory constraint.

---

## What I work on

**Constrained policy optimisation.** Fare-setting for a public autonomous mobility service is
a constrained Markov decision process, not an unconstrained one. The operator maximises profit
subject to an affordability standard that must hold in expectation over the deployed stochastic
policy. I work on two-critic PPO with a Lagrangian dual, on controllers that drive the dual
variable to its equilibrium without windup, and on the question of what the resulting multiplier
does and does not mean economically.

**Simulation environments.** Event-level models of a depot-based shared AV service: stochastic
request arrival, willingness-to-pay, sequential fare and waiting-time acceptance, vehicle
assignment, ride pooling, and persistent demand feedback. Built in Python on operator-supplied
demand data, with behavioural parameters calibrated to specified acceptance and elasticity
targets rather than estimated from revealed behaviour, and validated against analytical
references.

**Evaluation that survives contact with a reviewer.** Most of the engineering effort in my
projects goes here rather than into the learning algorithm. See below.

---

## Experimental practice

These are the standards I hold my own results to, and the part of the work I would most want a
reader to inspect.

**Seed roles are disjoint and enforced in code.** Training, checkpoint selection, calibration
and independent confirmation each draw from a separate seed block. The evaluator asserts that
the sets do not intersect before it will run. A checkpoint chosen on held-out seeds is frozen
before the confirmation seeds are touched, and a confirmation outcome never reopens the choice.

**Feasibility is tested, not asserted.** A policy counts as satisfying a constraint when the
one-sided 95% upper confidence bound on its constraint cost, estimated across independent
evaluation seeds, lies below the budget. That is statistical evidence under the evaluation
distribution, not a guarantee, and boundary cases are reported as boundary cases rather than
rounded into a pass.

**Comparisons are paired under common random numbers.** The random-number design is specified
down to draw order within the simulated hour, because matching integer seeds alone does not
reproduce an experiment. Where a family of comparisons is tested, p-values carry a Holm
step-down correction across the whole family.

**Results are bound to the code that produced them.** SHA-256 hashes over source files,
processed inputs, scenario manifests and result archives. A reported number can be traced to an
executed build.

**The simulator is validated against things with known answers.** The queueing core is checked
against Erlang-C waiting times at 75% utilisation; accounting identities and vehicle
conservation are asserted at every episode.

---

## Research projects

| Project | Description | Status |
| --- | --- | --- |
| [`cmdp-affordability-pricing`](https://github.com/elias-zigah/cmdp-affordability-pricing) | Constrained deep RL for dynamic pricing under a long-run affordability budget. Two-critic PPO, Lagrangian dual with PI control, 12 policy instances trained to 20M steps. | Manuscript under review |
| [`fare-flexibility-fleet-capacity`](https://github.com/elias-zigah/fare-flexibility-fleet-capacity) | How much fleet capacity regulated fare flexibility can replace under a service-reliability standard. 23,630 month-long simulation runs across a staged selection and confirmation protocol. | Manuscript under review |

Each repository currently holds a reproducibility record describing the study, its protocol and
its results. Code and replication archives are planned for release following manuscript
acceptance, subject to data-sharing permissions. Input data supplied by operating partners is not
redistributable; repositories will ship access instructions and checksums in its place.

---

## Selected publications

- **Dynamic Pricing for Shared Autonomous Vehicles in Mobility-as-a-Service: An Integrative
  Review of Models, Performance, and Policy Trade-offs.** *Transportation Research Procedia*
  (2025).
- **An Evaluation of Dynamic Pricing Methodologies for Publicly Managed Shared Autonomous
  Vehicle Services.** Under review, *Transportation Research Interdisciplinary Perspectives*.
- **Constrained Markov decision process for dynamic pricing under long-run affordability
  requirements.** Submitted, *Transportation Research Part B*.
- **How much fleet capacity can regulated fare flexibility replace under a service reliability
  standard?** Submitted, *Transportation Research Part E*.
- **Are Mini-Grid Projects in Tanzania Financially Sustainable?** In *Electricity Access,
  Decarbonization, and Integration of Renewables*, Springer VS (2023).

---

## Tooling

Python · PyTorch · Stable-Baselines3 · NumPy · pandas · SciPy · SLURM / HPC · Git

---

## Elsewhere

[Google Scholar](https://scholar.google.com/citations?user=<your-scholar-id>) ·
[LinkedIn](https://www.linkedin.com/in/elias-zigah/) ·
[ORCID](https://orcid.org/<0000-0002-3363-9041>)
