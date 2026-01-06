# Create Pull Request

Current branch:
!git branch --show-current

Commits to push:
!git log --oneline origin/master..HEAD 2>/dev/null || git log --oneline -3

Push the current branch and create a pull request with a clear title and description.

After creating the PR, check the CI status and report any failures.
