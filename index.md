---
layout: default
---

# A GitHub API client library written in POSIX sh

## Requirements

* A POSIX environment (tested against Busybox v1.19.4)
* curl (tested against 7.32.0)

## Optional requirements

* jq <http://stedolan.github.io/jq/> (tested against 1.3)
  If jq is not installed commands will output raw JSON; if jq is installed
  commands can be pretty-printed for use with other shell tools.

## Setup

Authentication credentials are read from a ~/.netrc file with the following
format. Generate the token on GitHub under Account Settings -> Applications.
Restrict permissions on that file with `chmod 600 ~/.netrc`!

    machine api.github.com
        login <username>
        password <token>

## Configuration

The following environment variables may be set to customize octokit.sh.

* OCTOKIT_SH_URL=https://api.github.com
  Base URL for GitHub or GitHub Enterprise.
* OCTOKIT_SH_ACCEPT=application/vnd.github.v3+json
  The 'Accept' header to send with each request.
* OCTOKIT_SH_JQ_BIN=jq
  The name of the jq binary, if installed.
* OCTOKIT_SH_VERBOSE=0
  The debug logging verbosity level. Same as the verbose flag.
* OCTOKIT_SH_RATE_LIMIT=0
  Output current GitHub rate limit information to stderr.
* OCTOKIT_SH_DESTRUCTIVE=0
  Allow destructive operations without prompting for confirmation.

## Usage

Usage: `octokit.sh [<options>] (command [<name=value>...])`

Full help output: `octokit.sh help`
Command-specific help: `octokit.sh help command`

Flag | Description
---- | -----------
-V   | Show version.
-h   | Show this screen.
-j   | Output raw JSON; don't process with jq.
-q   | Quiet; don't print to stdout.
-r   | Print current GitHub API rate limit to stderr.
-v   | Logging output; specify multiple times: info, debug, trace.
-x   | Enable xtrace debug logging.
-y   | Answer 'yes' to any prompts.

## Available commands

help, show_scopes, org_repos, org_teams, list_repos, create_repo, delete_repo, 
list_releases, release, create_release, delete_release, release_assets, 
upload_asset

### Full documentation for each command

{% for page in site.pages %}
  {% if page.url == '/path/to/page.html' %}
[{{ page.title }}]({{ page.url }})
  {% endif %}
{% endfor %}
