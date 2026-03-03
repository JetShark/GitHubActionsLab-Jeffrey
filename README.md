# GitHub Actions Lab: Automating Workflows

![Ubuntu](https://img.shields.io/badge/Ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white)
![Windows](https://img.shields.io/badge/Windows-0078D6?style=for-the-badge&logo=windows&logoColor=white)
![macOS](https://img.shields.io/badge/macOS-000000?style=for-the-badge&logo=apple&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-232F3E?style=for-the-badge&logo=amazon-aws&logoColor=white)

This repository serves as a technical showcase for modern CI/CD patterns and best practices using **GitHub Actions**, demonstrating three core workflows that focus on environment security, multi-platform validation, and architectural job dependencies across **Ubuntu**, **Windows**, and **macOS**, including secure integration with **AWS / GitHub Secrets**.

---

## Workflows Overview

### 1. [Dependent Jobs Workflow](.github/workflows/dependent-jobs.yml)
*   **Trigger**: Automatic on `push` to `main`.
*   **Focus**: Job dependencies and sequential execution.
*   **Process**: Simulates a full lifecycle: `Build` → `Test` → `Deploy`. Each stage must succeed for the next to begin, demonstrated using the `needs` keyword.

### 2. [Environment Variables and Secrets](.github/workflows/env-and-secrets.yml)
*   **Trigger**: Manual via `workflow_dispatch`.
*   **Focus**: Scoping and Security.
*   **Key Features**: 
    - Demonstrates **Workflow**, **Job**, and **Step** level environment variables.
    - Showcases secure handling of **GitHub Secrets** (AWS Keys) with automatic masking in logs.
    - Includes a job dependency to verify how variables lose scope across different job boundaries.

### 3. [Multi-Platform Testing](.github/workflows/multi-platform.yml)
*   **Trigger**: Automatic on `pull_request` to `main`.
*   **Focus**: Parallel execution and OS-specific behavior.
*   **Configuration**: Simultaneously validates code on three unique runners:
    - 🐧 **Linux**: Native Bash with kernel auditing.
    - ⊞ **Windows**: PowerShell Core with `Get-ComputerInfo` diagnostics.
    - 🍎 **macOS**: Zsh environment with `sw_vers` validation.
*   **Details**: Uses **native commands** for each OS (e.g., `sw_vers`, `Get-ComputerInfo`, `df -h`) to log system information and validate file system operations across platforms.