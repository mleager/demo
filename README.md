# Demo Repository

terraform/:
===========

Basic terraform example used to test workflows (.github/workflows)


workflows/:
===========

For testing before migrating to .github/workflows

Current workflows:
------------------

- creates development, staging, and production environments

- creates basic branch protections

- examples of deploying to development, staging, and production


json/:
======

JSON files for API calls


-------------------------------------------------------------------------------


## Purpose

Develop workflow for multiple environments

1. create feature/hotfix/bugfix branch from long-lived development branch

- environment: development

- branch protections: minimal (requires PR approval)


2. after successful deployment to development, merge PR to staging branch

- environment: staging

- branch protections: medium (requires PR approval, linear history, etc.)


3. after successful deployment to staging, merge PR to main

- environment: production

- branch protections: high (cannot delete, read only, etc.)


-------------------------------------------------------------------------------


## Repo Structure

Long-lived Branches: development, staging, main
Environments: development, staging, production

Features, fixes, chores, etc. are branched off from development branch

PR from feature/* to development branch

Merge, then deploy development environment workflow on development branch

After successul deployment, PR from development to staging

Merge, then deploy staging environment workflow (testing, etc.) on staging branch

After successful deployment, PR and from staging to main - deploy to production

-------------------------------------------------------------------------------


## Example (review later)

1. Create feature or task specific branch from the development branch

- create branch: feature/login, hotfix/user-auth, etc.


2. PR to Development branch (add features, fix bugs, etc.) --> Run Workflow

- push feature/login to development branch and deploy actions workflow to the development environment


3. Development Workflow Succeeds --> Merge to Staging

- when successful deploy, make a PR from development to staging environment


2. Staging Workflow Succeeds --> PR to Main

- when successfully deployed to staging, make a PR to main


3. Merge Staging to Main (has restrictive branch protections)

-------------------------------------------------------------------------------


[1] Feature branch (dev/feature-login)
        ↓ PR
[2] Merge into development → Deploy to Development Env
        ↓ PR
[3] Merge into staging → Deploy to Staging Env
        ↓ PR
[4] Merge into main → Deploy to Production (requires approval)

-------------------------------------------------------------------------------

## Developer Workflow Example

1. Branch off of Development

```bash
git checkout development
git pull origin development
git checkout -b feature/login
```


2. Commit and Push

```bash
git add .
git commit -m "add login feature"
git push origin feature/login
```


3. Create PR -> Target: development branch

Compare & Pull Request

- base branch: development
- compare branch: feature/login


4. Merge PR after Review

Deploy actions workflow to development environment


5. Move to Staging

Create a new PR to push development to staging (2 strategies)

After enough features are ready, create a PR

```bash
git checkout staging
git pull origin staging
git merge development
git push origin staging
```

