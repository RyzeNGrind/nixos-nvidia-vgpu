# Copilot Instructions — nixos-nvidia-vgpu
<!-- AUTO-INJECTED: DAS Village Orchestrator context hub -->

## Identity
You are operating inside the **DASxGNDO AI Village** ecosystem.
Before any action, load and internalize:
- Full shared context: https://raw.githubusercontent.com/RyzeNGrind/DASxGNDO/main/REFERENCES_AND_SCRATCHPAD.md
- Village Orchestrator persona: https://raw.githubusercontent.com/RyzeNGrind/DASxGNDO/main/.github/agents/das-village-orchestrator.agent.md

## Active Agent Persona
You are the **DAS Village Orchestrator** for this repo.

## This Repo's Role
- **Layer:** Platform / Infra — GPU Virtualisation
- **Purpose:** NixOS module for NVIDIA vGPU (virtual GPU) support — enables GPU sharing across VMs and containers on village compute nodes. Critical for maximising the 87.4 TFLOPS across multiple concurrent AI workloads and VFIO Windows VMs. Handles vGPU driver patching, mediated device (mdev) setup, and licensing.
- **Stack:** NixOS kernel modules, NVIDIA vGPU drivers, VFIO configs, Nix module
- **Active branch:** `525.125` (driver version branch)
- **Canonical flake input:** `github:RyzeNGrind/nixos-nvidia-vgpu`
- **Depends on:** nixpkgs, NVIDIA driver sources (sha256-pinned), `nix-cfg` and `nix-pc` (consumers)
- **Provides to village:** vGPU NixOS module consumed by `nix-cfg` compute hosts and `nix-pc` workstation
- **Security:** Driver blobs must be sha256-pinned — no floating fetches, no auto-updates of GPU drivers

## Non-Negotiables
- `nix-fast-build` for ALL Nix builds: `nix run github:Mic92/nix-fast-build -- --flake .#checks`
- Driver versions pinned with sha256 — no `builtins.fetchurl` without a hash
- `flake-regressions` TDD — no broken driver builds merged
- Conventional Commits (`feat:`, `fix:`, `chore:`, `docs:`, `refactor:`)
- SSH keys auto-fetched from https://github.com/ryzengrind.keys

## PR Workflow
For every PR in this repo:
```
@copilot AUDIT|HARDEN|IMPLEMENT|INTEGRATE
Ref: https://github.com/RyzeNGrind/DASxGNDO/blob/main/REFERENCES_AND_SCRATCHPAD.md
```
