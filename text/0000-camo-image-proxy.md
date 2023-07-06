*   2023-07-04
*   Scope: `rehypejs/rehype-github` (or new repository)
*   RFC PR: <!-- leave this empty -->
*   Implementation issue(s): <!-- leave this empty -->

# Summary

A new Node.js HTTP proxy to route images through SSL, compatible with unified
plugins, to safely embed user content on the web.

Implementation would be done by me and would require funds from Open Collective.

## Motivation

Unified has put a lot of effort in providing similar markdown support as GitHub.
The latest project, [`rehype-github`][], takes this even further in order to
support processing user content for safe use on the web, just as GitHub does.

There is a missing piece in safely authoring user content: images.

> An HTTPS page that includes content fetched using cleartext HTTP is called a
> mixed content page.  Pages like this are only partially encrypted, leaving the
> unencrypted content accessible to sniffers and man-in-the-middle attackers.
> — [MDN](https://developer.mozilla.org/en-US/docs/Web/Security/Mixed_content)

Developers aware of this problem, who are using Go or are willing to run a Go
server, can use the well maintained [go-camo][] to solve this.  However, there
is no Node.js equivalent, nor is there a plug-and-play solution for processing
markdown which takes this problem into account.

Case in point: a new Node.js HTTP proxy to route images through SSL, and a
unified plugin to rewrite image URLs to use this proxy if necessary.

It’s in the ecosystem’s and the web’s best interest to create awareness and
solutions for security problems when authoring user content.

## Detailed design

*   A bare bones Node.js server (no framework).
    The reason for this is that we can create a `handle` function which can be
    integrated in any Node.js framework or even a front-end framework
    like Next.js.  This is what I’ve worked on for `@tus/server`,
    as you can see in the [examples](https://github.com/tus/tus-node-server/tree/main/packages/server#examples).
*   A client-server flow similar to this:

```text
  +----------+           request            +-------------+
  |          |----------------------------->|             |
  |          |                              |             |
  |          |                              |   web-app   |
  |          | img src=https://camo/url     |             |
  |          |<-----------------------------|             |
  |          |                              +-------------+
  |  client  |
  |          |     https://camo/url         +-------------+ http://some/img
  |          |----------------------------->|             |--------------->
  |          |                              |             |
  |          |                              |   camo      |
  |          |           img data           |             |    img data
  |          |<-----------------------------|             |<---------------
  |          |                              +-------------+
  +----------+
```

*   A new plugin in \[`rehypejs/rehype-github`]\[] to rewrite image URLs to use
    this proxy if necessary.
*   Out of scope (for now): metrics endpoint for usage data, filtering rules.

## Funding

In short: between $500 and $1,000 from Open Collective (exact amount up for
debate).

*   **Why take money at all?**
    *   I’m not really in a position to do this for free.  I make my living from
        maintaining open source software on freelance basis and life is also
        busy.  To really push this through I would put other paid work on hold.
    *   Since there is no
        [expenses/invoices/fund policy](https://github.com/unifiedjs/collective/issues/34),
        taking money from Open Collective is not clearly defined.
        But here is how I ideally imagine it:
        funds are used to kick start substantial work which
        otherwise may not have happened.  Many people maintain OSS for free
        (and thanklessly) but we also shouldn’t be afraid to ask for funds.
        There is at the time of writing $23,648 in Open Collective.
        It’s not a lot if you want to live from it,
        but it is a lot if you would divide it by the amount of
        projects it could kick start.
*   **Why me?**  I have experience in creating Node.js servers at scale and
    globally distributed.  I also maintain [tus](https://tus.io/), a protocol
    for resumable file uploads in multiple languages.
*   **Why this amount of $**?  With implementation, tests, and docs, this could
    take around three full days (optimistically).  Naturally, I didn’t base this
    on a freelance rate I work for normally.  It’s more an attempt at a fair
    flat fee.

## Drawbacks

*   Money out of the Open Collective.
*   [go-camo][] already exists so there is some solution to this problem.
    But for people with front-end frameworks or Node.js servers this would mean
    hosting another server.  Furthermore unified could contribute to awareness
    of the problem and a streamlined plug-and-play experience.

## Alternatives

*   Only creating a unified plugin compatible with [go-camo][].  This would take
    significantly less effort and no funds.  It would still leave the Node.js
    ecosystem without a solution.
*   Not doing anything, only writing about the problem.

## Adoption strategy

Not relevant since it is a new project.

[`rehype-github`]: https://github.com/rehypejs/rehype-github

[go-camo]: https://github.com/cactus/go-camo
