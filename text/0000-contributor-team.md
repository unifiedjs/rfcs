- Start Date: 2019-02-27
- RFC PR:
- unified Issue:

# Summary

It'd be nice to add a "contributor" team to unified organizations which
all contributors are invited to. There's precedent here with what Gatsby
does and helps contributors receive a warm welcome to the community after
getting a PR merged.

## Basic example

If a user gets a PR merged they receive an invite to the org as a "contributor".
The contributor team doesn't have write access.

## Motivation

To make contributors feel welcome.

## Detailed design

We can use a GitHub Action (once unified orgs have access) to check if the new
contributor is part of the org and add them if they aren't to the contributor
team.

## Drawbacks

None that I can see.

## Alternatives

- GitHub contribution graph
- [all-contributors](https://github.com/all-contributors/all-contributors)

## Adoption strategy

N/A

## Unresolved questions

- What (if any) access do read-only members have to GitHub integrated platforms? (Zeit Now, Travis CI, etc)
