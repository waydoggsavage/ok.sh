---
layout: default
title: Repository Functions
---

### org_repos()

List organization repositories

Usage:

    org_repos myorg
    org_repos myorg type=private per_page=10
    org_repos myorg filter='.[] | "\(.name)\t\(.owner.login)"'

Positional arguments

* org : $1
  Organization GitHub login or id for which to list repos.

Keyword arguments

* type : all
  Filter by repository type. all, public, member, sources, forks, or
  private.
* per_page : 100
  The number of repositories to return in each single request.
* filter : '.[] | "\(.name)\t\(.ssh_url)"'
  A jq filter using string-interpolation syntax that is applied to each
  repository in the return data.

### org_teams()

List teams

Usage:

    org_teams org

Positional arguments

* org : $1
  Organization GitHub login or id.

Keyword arguments

* filter : '.[] | "\(.name)\t\(.id)\t\(.permission)"'
  A jq filter using string-interpolation syntax that is applied to each
  team in the return data.

### list_repos()

List user repositories

Usage:

    list_repos
    list_repos user

Positional arguments

* user : $1
  Optional GitHub user login or id for which to list repos.

Keyword arguments

* filter : '.[] | "\(.name)\t\(.html_url)"'
  A jq filter using string-interpolation syntax that is applied to each
  repository in the return data.

type, sort, direction

### create_repo()

Create a repository for a user or organization

Usage:

    create_repo foo
    create_repo bar description='Stuff and things' homepage='example.com'
    create_repo baz organization=myorg

Positional arguments

* name : $1
  Name of the new repo

Keyword arguments

* filter : '.[] | "\(.name)\t\(.html_url)"'

description, homepage, private, has_issues, has_wiki, has_downloads,
organization, team_id, auto_init, gitignore_template

### delete_repo()

Create a repository for a user or organization

Usage:

    delete_repo owner repo

The currently authenticated user must have the `delete_repo` scope. View
current scopes with the `show_scopes()` function.

Positional arguments

* owner : $1
  Name of the new repo
* repo : $2
  Name of the new repo
