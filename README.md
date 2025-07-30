# Commit Hooks – Detailed Documentation

![commit hook](https://github.com/user-attachments/assets/72fb696e-b86f-4744-9cfe-cfb31ebb0f97)

---

## Author Information
| Last Updated On | Version | Author           | Level           | Reviewer               |
|-----------------|---------|------------------|-----------------|------------------------|
| 29-07-2025      | V1.0    | Kawalpreet Kour  | Internal Review | Pritam                 |
|                 |         | Kawalpreet Kour  | L0              | Shreya/Sharvani        |
|                 |         | Kawalpreet Kour  | L1              | Abhishek V             |
|                 |         | Kawalpreet Kour  | L2              | Abhishek Dubey/Rishabh Sharma |

---

<details>
  <summary><strong>Table of Contents</strong></summary>

- [Introduction](#introduction)  
- [Purpose of Commit Hooks](#purpose-of-commit-hooks)  
- [Types of Commit Hooks](#types-of-commit-hooks)  
  - [Client-side Hooks](#1-client-side-hooks)  
  - [Server-side Hooks](#2-server-side-hooks)  
- [How to Use Git Hooks](#how-to-use-git-hooks)  
- [FAQ](#faq)  
- [Contact Information](#contact-information)  
- [References](#references)  

</details>

---

## Introduction

Commit hooks (also known as Git hooks) are scripts that run automatically at certain points in the Git workflow. They help enforce standards, perform checks, or automate tasks during development processes such as commits, merges, or pushes.

---

## Purpose of Commit Hooks

- Enforce code quality and formatting before commits  
- Prevent bad commits or pushes (e.g., failed tests, linting issues)  
- Automate tasks like running tests, checking secrets, or validating commit messages  
- Improve collaboration and CI/CD pipeline reliability  

---

## Types of Commit Hooks

Git provides two types of hooks:

### 1. Client-side Hooks
Executed on the developer's machine. Used to:

- Format code  
- Run linters/tests  
- Validate commit messages  

**Common Client Hooks:**

| Hook Name            | Trigger Point                        | Use Case Example                          |
|----------------------|--------------------------------------|-------------------------------------------|
| `pre-commit`         | Before a commit is finalized         | Run linting or formatting tools           |
| `prepare-commit-msg` | Before the commit message editor opens | Add JIRA ticket ID to message          |
| `commit-msg`         | After the message is written         | Validate commit message format            |
| `pre-push`           | Before changes are pushed            | Run tests or checks                       |

---

### 2. Server-side Hooks
Run on the remote Git server. Used to:

- Validate pushes  
- Enforce team-level policies  

**Common Server Hooks:**

| Hook Name      | Trigger Point                   | Use Case Example                            |
|----------------|----------------------------------|---------------------------------------------|
| `pre-receive`  | Before changes are accepted      | Block pushes that fail tests                |
| `update`       | Before branch refs are updated   | Check commit messages                       |
| `post-receive` | After push is completed          | Trigger CI/CD pipelines                     |

---

## How to Use Git Hooks

1. Navigate to your Git project’s `.git/hooks` directory:
   ```bash
   cd your-repo/.git/hooks
   ```

2. Copy and rename a sample hook:
   ```bash
   cp pre-commit.sample pre-commit
   ```

3. Edit the hook script:
   ```bash
   nano pre-commit
   ```

4. Add your script (e.g., run tests or format check), then save.

5. Make it executable:
   ```bash
   chmod +x pre-commit
   ```

6. Test it by making a commit:
   ```bash
   git commit -m "Test hook"
   ```

> You can also use tools like **Husky (for JavaScript projects)** or **Lefthook** for cross-language hook management.

---

## FAQ

**Q1: Are commit hooks shared across developers?**  
*A1: Not by default. Hooks live in `.git/hooks` which is not committed. Use tools like Husky or dotfiles repo to share hooks.*

**Q2: Can hooks block commits?**  
*A2: Yes, `pre-commit` and `commit-msg` can return a non-zero exit to block the commit.*

**Q3: Are Git hooks supported in GUI tools like GitHub Desktop?**  
*A3: Generally no. GUI tools may skip local hooks unless explicitly configured.*

---

## Contact Information

| Name             | Email                                         |
|------------------|-----------------------------------------------|
| Kawalpreet Kour  | Kawalpreet.kour.snaatak@mygurukulam.co        |

---

## References

| Link                                                                                                           | Description                                      |
|----------------------------------------------------------------------------------------------------------------|--------------------------------------------------|
| [https://www.atlassian.com/git/tutorials/git-hooks](https://www.atlassian.com/git/tutorials/git-hooks)         | Atlassian Git Hooks Tutorial                     |
| [https://www.geeksforgeeks.org/git/git-hooks/](https://www.geeksforgeeks.org/git/git-hooks/)                   | GeeksforGeeks Guide on Git Hooks                |
