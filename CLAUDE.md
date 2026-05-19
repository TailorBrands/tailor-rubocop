# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Purpose

This repository contains a single shared RuboCop configuration file (`rubocop.yml`) used by all TailorBrands Ruby microservices. Services reference this file directly (typically via a URL or by copying it) to enforce consistent Ruby style across the organization.

## Repository Structure

- `rubocop.yml` — 6,400+ line master RuboCop config covering all cop categories (Bundler, Gemspec, Layout, Lint, Metrics, Migration, Naming, Performance, RSpec, Security, Style). Includes the `rubocop-rspec` plugin.

## Working with the Config

**This repo has no build step, test suite, or package manager.** Changes consist solely of editing `rubocop.yml`.

Key facts about the file:
- `AllCops` section at the top sets global defaults (file includes/excludes, formatting options, `TargetRubyVersion: ~` meaning version is auto-detected per project).
- 514 cops are explicitly enabled; 84 are explicitly disabled. When adding or changing a cop, match the existing format: `Description`, `Enabled`, any parameter overrides, `VersionAdded`/`VersionChanged`.
- RSpec cops (`RSpec/`) are included via the `rubocop-rspec` plugin declared at the top of the file.

## Making Changes

1. Edit `rubocop.yml` directly — find the relevant cop section (file is alphabetical within each category).
2. To disable a cop org-wide: set `Enabled: false` under its entry.
3. To relax a threshold (e.g. `Metrics/MethodLength`): add or update the `Max:` parameter.
4. PRs auto-notify teams on merge via the `pr_merged_notification` workflow.
