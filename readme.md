# unified RFCs — [List of active RFCs][active]

“Substantial” initiatives in the unified collective, such as those affecting
multiple projects or organizations, are made through **RFCs** (request for
comments).
How members of the collective make decisions, and when an RFC is appropriate, is
described in our [governance docs][decisions] (includes a flowchart!)
This document described how to request, discuss, decide, and implement RFCs.

Please understand that an RFC is a *request for comments*, with an emphasis on
the discussion of potential proposals.
It is understood and, in fact, *expected* that members will have and express
individual opinions.
Quite often, even proposals that seem “obvious” can be significantly improved
once a wider group of interested people have a chance to weigh in.

## Table of contents

*   [Process](#process)
    *   [Request](#request)
    *   [Discuss](#discuss)
    *   [Decide](#decide)
    *   [Implement](#implement)
*   [Acknowledgements](#acknowledgements)

## Process

In short, create a Markdown file describing the initiative and open a pull
request.
Then, discussion of potential proposals is held, followed by the framing of a
solution, and then modifying it until the group reaches a consensus.
The pull request is merged, making the RFC is active, after which it may be
implemented.

### Request

*   [Fork the RFC repository][fork]
*   Copy `0000-template.md` to `text/0000-my-proposal.md` (where `my-proposal`
    is descriptive; don’t assign an RFC number quite yet)
*   Fill in the RFC.
    Put care into the details: RFCs that do not present convincing motivation,
    demonstrate an understanding of the impact of the design, or are
    disingenuous about the drawbacks or alternatives tend to be
    poorly-received
*   Submit a pull request

### Discuss

*   Engage in the discussion!
    The RFC will receive feedback from the community, and the author should be
    prepared to revise it in response
*   Build consensus and integrate feedback.
    RFCs that have broad support are much more likely to make progress
*   Eventually, the team decides whether the RFC is a candidate for inclusion,
    and your proposal will enter a **final comment period** lasting for three
    days (72 hours).
    The beginning of this period will be signaled with a comment.
    Further comments may result in a new final comment period

### Decide

*   An RFC may be rejected by the team after the discussion has settled and
    comments have been made summarizing the rationale for rejection.
    The pull request is closed
*   An RFC may be accepted at the close of its final comment period.
    The pull request is merged and assigned an RFC number, at which point the
    RFC will become **active**.
    Congrats!

### Implement

When an RFC is active, persons may implement solutions and submit pull requests.
Becoming **active** is not a rubber stamp, and in particular still does not mean
solutions will ultimately be included; it does mean that maintainers have agreed
and in principle and are amenable to included them.

The fact that an RFC is “active” implies nothing about what priority is assigned
to its implementation, nor whether anybody is currently working on it.

The author of an RFC is not obligated to implement it.

Modifications to active RFCs can be done in followup pull requests.
We strive to write each RFC in a manner that it will reflect the final design,
but the nature of the process means that we cannot expect all RFCs to actually
reflect the end result.
Followup pull requests should be created to amend the RFC if it is no longer in
sync with its implementation.

## Acknowledgements

The unified RFC process owes its inspiration to the [Gatsby RFC process][],
[React RFC process][], [Yarn RFC process][], [Rust RFC process][], and [Ember
RFC process][].

[active]: https://github.com/unifiedjs/rfcs/issues?q=label%3A%22🥂+status%2Fmerged%22+is%3Aclosed

[decisions]: https://github.com/unifiedjs/governance/blob/master/decisions.md

[fork]: http://github.com/unifiedjs/rfcs

[gatsby rfc process]: https://github.com/gatsbyjs/rfcs

[react rfc process]: https://github.com/reactjs/rfcs

[yarn rfc process]: https://github.com/yarnpkg/rfcs

[rust rfc process]: https://github.com/rust-lang/rfcs

[ember rfc process]: https://github.com/emberjs/rfcs
