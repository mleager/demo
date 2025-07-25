# demo/workflows

Basic example workflows for:
- creating environments (development, staging, production)
- creating branch protections
- deployments for each environment


TODO: implement flow for push and PR branch
- run workflow in development when PR from feature/* to development branch
- run workflow in staging when PR from development to staging
- run workflow in production when PR from staging to main


setup-repo-environments-and-protections.yml
===========================================

- create 3 environments
- development, staging, production
- (needs better branch protections)


deploy-development.yml
======================

- terraform plan
- terraform apply


deploy-staging.yml
==================

- tests, scanning, etc.
- terraform plan
- terraform apply


deploy-production.yml
=====================

- readiness check
- terraform plan
- terraform apply
- health checks

