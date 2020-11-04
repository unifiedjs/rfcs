*   Start date: 2020-11-04
*   Scope: Collective
*   RFC PR: <!-- leave this empty -->
*   Implementation issue(s): <!-- leave this empty -->

# Summary

It’s becoming harder to handle the incoming stream of questions and issues, so I
thought I’d open a discussion to talk about how to tackle that.

Bots may help.

This is a conversation starter: **I’m curious to hear what y’all think would
(not) be useful**.

## Motivation

It’s becoming harder to handle the incoming stream of questions and issues, so I
thought I’d open a discussion to talk about how to tackle that.

I’m assuming this is coming from a couple of places:

*   unified is becoming more popular
*   MDX, recently react-markdown, and potentially more in the future, joined
*   [Discussions](https://github.blog/2020-05-06-new-from-satellite-2020-github-codespaces-github-discussions-securing-code-in-private-repositories-and-more/#discussions) is an easy way for folks to ask questions

Regardless of why, a different type of user is reaching unified (an exemplary
question yesterday was: “why are there margins on my `<p>`”,
[remarkjs/react-markdown#503](https://github.com/remarkjs/react-markdown/issues/503)).
A lot of these questions are XY problems and result in maintainers acting like
a rubber duck for three back-and-forths.

I hope that automation can help deal with the flow of incoming questions so that
maintainers can stay healthy.

## Detailed design

For a solution, here are a couple broad ideas:

*   Improve docs on unifiedjs.com (important, but to be discussed somewhere
    else)
*   Improve contributing, support, and issue templates
*   Shared saved responses (see
    <https://github.com/electron/governance/tree/master/playbooks/responses>
    and
    <https://github.com/electron/electron/issues?q=is%3Aissue+is%3Aclosed>)
*   Add automation/bots

Specifically, for automation, I’m thinking:

*   Enforce filled out issue/pr/discussion templates
*   “Lint” issue checklists: if someone is on an old Node, respond and close
    that those aren’t supported; or enforce that
    `* [ ] I promise to adhere to the code of conduct` is checked
*   Automate [label](https://github.com/unifiedjs/github-tools/labels)/issue
    interplay:
    if maintainer adds `type/question`, the issue is closed and a predefined
    response posted to ask in discussions instead;
    `platform/*` can be found from the issue checklist;
    merging can add `status/merge`, or `status/wontfix` can close one;
    `area/*` could be added to the issue title?
*   Maybe difficult, but: GH has support for finding similar issues, but doesn’t
    scan all our repos (or discussions), maybe we can do that ourselves: respond
    on an issue with similar issues?
*   Lock old issues

I’m thinking this can be done in GH actions, which seems to be pretty fast.
That does mean the action must be added to all repos, but then it’s also a nice
opt-in.
And actions are free (which is also a drawback, but GH seems to impose limits
per repo instead of user, and they have deep pockets).

## Drawbacks

It’s a bit sad to “outsource” to bots and loose the “human connection”.

## Alternatives

*   Burning out maintainers.
*   Finding more folks to triage.
    GitHub now highlights the number of answered discussions on user profiles,
    which might encourage more folks to help

## Adoption strategy

*   Discuss
*   Make it
*   Add actions to repos, through manual opt-in, or through workflow templates:
    <https://docs.github.com/en/free-pro-team@latest/actions/learn-github-actions/sharing-workflows-with-your-organization>

## Unresolved questions

Everything.
