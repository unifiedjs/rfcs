*   Start date: 2019-02-27
*   Scope: the collective
*   RFC PR: [2][]
*   Implementation issue(s): [`unifiedjs/github-tools#7`][issue] and
    [`unifiedjs/github-tools#8`][pr]

# Summary

It’d be nice to add a “contributor” team to unified organizations that all
contributors are invited to.
There’s precedent here with what Gatsby does and helps contributors receive a
warm welcome to the community after getting a PR merged.

## Basic example

If a user gets a PR merged they receive an invite to the org as a “contributor”.
The contributor team has triage (not write) access on GitHub.

## Motivation

To make contributors feel welcome.

## Detailed design

*   [Motion to nominate a contributor][motion]
*   [`github-tools`][tools]

## Drawbacks

*   Could grow into 100s of inactive contributors

## Alternatives

*   GitHub contribution graph
*   [`all-contributors`][all-contributors]

## Adoption strategy

N/A

## Unresolved questions

N/A

[2]: https://github.com/unifiedjs/rfcs/pull/2

[issue]: https://github.com/unifiedjs/github-tools/issues/7

[pr]: https://github.com/unifiedjs/github-tools/pull/8

[motion]: https://github.com/unifiedjs/collective/blob/master/members.md#motion-to-nominate-a-contributor

[tools]: https://github.com/unifiedjs/github-tools

[all-contributors]: https://github.com/all-contributors/all-contributors
