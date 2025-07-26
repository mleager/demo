# demo/json

create-branch-protections-api.json
==================================

- create basic branch protection using API
- intended for workflow job

```bash
curl -L \
  -X PUT \
  -H "Accept: application/vnd.github+json" \
  -H "Authorization: Bearer <YOUR-TOKEN>" \
  -H "X-GitHub-Api-Version: 2022-11-28" \
  https://api.github.com/repos/OWNER/REPO/branches/BRANCH/protection \
  -d @create-branch-protections-api.json
```


get-branch-protection-*.json
============================

- results of calling the API on 2 diferrent branches
- used for testing and comparisons


update-branch-protection-example.json
=====================================

- sample api call from github api docs
- some fields are for organzation only


update-pr-access-only.json
==========================

- json data for only updating the PR Access field
- requires specific API path


ruleset-demo-dev.json
=====================

- results of exporting basic ruleset
- can be imported to other repos

