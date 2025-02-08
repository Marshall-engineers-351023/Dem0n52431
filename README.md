- 👋 Hi, I’m @Dem0n52431
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
- Hello Alice ❄️

- GUI-related pull requests should be opened against

-
@primer/react v37.11.2
<!---
Dem0n52431/Dem0n52431 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
org:rails


Phi-3-medium instruct (128k)


$ git merge upstream/main
> Updating 34e91da..16c56ad
> Fast-forward
>  README.md                 |    5 +++--
>  1 file changed, 3 insertions(+), 2 deletions(-)

1801-forks








@primer/react v37.11.2






# Template to sync with upstream
name: Sync Upstream

env:
  # Required, URL to upstream (fork base)
  UPSTREAM_URL: "https://github.com/<usr>/<repo>.git"
  # Required, token to authenticate bot, could use ${{ secrets.GITHUB_TOKEN }} 
  # Over here, we use a PAT instead to authenticate workflow file changes.
  WORKFLOW_TOKEN: ${{ secrets.WORKFLOW_TOKEN }}
  # Optional, defaults to main
  UPSTREAM_BRANCH: "main"
  # Optional, defaults to UPSTREAM_BRANCH
  DOWNSTREAM_BRANCH: ""
  # Optional fetch arguments
  FETCH_ARGS: ""
  # Optional merge arguments
  MERGE_ARGS: ""
  # Optional push arguments
  PUSH_ARGS: ""
  # Optional toggle to spawn time logs (keeps action active) 
  SPAWN_LOGS: "false" # "true" or "false"

# This runs every day on 1801 UTC
on:
  schedule:
    - cron: '1 18 * * *'
  # Allows manual workflow run (must in default branch to work)
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: GitHub Sync to Upstream Repository
        uses: dabreadman/sync-upstream-repo@v1.3.0
        with: 
          upstream_repo: ${{ env.UPSTREAM_URL }}
          upstream_branch: ${{ env.UPSTREAM_BRANCH }}
          downstream_branch: ${{ env.DOWNSTREAM_BRANCH }}
          token: ${{ env.WORKFLOW_TOKEN }}
          fetch_args: ${{ env.FETCH_ARGS }}
          merge_args: ${{ env.MERGE_ARGS }}
          push_args: ${{ env.PUSH_ARGS }}
          spawn_logs: ${{ env.SPAWN_LOGS }}
