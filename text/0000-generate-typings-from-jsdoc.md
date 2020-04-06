*   Start date: 2020-04-05
*   Scope: collective
*   RFC PR: <!-- leave this empty -->
*   Implementation issue(s): <!-- leave this empty -->

# Summary

Generate TypeScript typings from JSDoc.

## Basic example

An example of this can be seen at <https://github.com/vfile/vfile-message/pull/8>.

## Motivation

Currently typings are hand generated based off reviewing the API documentation.
As changes to the API are made, the typings need to be updated, but there is currently no mechanism in place that checks that the two still match.
This can cause drift between what the API actually does and what the typings say the API does.

The goal is to close the gap between the source, the API, and the typings keeping them in sync.

## Detailed design

TypeScript supports checking types and generating typings files based off [JSDoc comments](https://jsdoc.app). <https://www.typescriptlang.org/docs/handbook/type-checking-javascript-files.html>

Using documentation comments with TypeScript has several advantages:
1. It allows TypeScript to validate the typings match the source
2. It keeps comments in the code in sync with comments in the typings (used by IDEs that support TypeScript)
3. It keeps the source in JavaScript
   1. Allowing the repository to be added as a dependency directly from git
   2. Avoiding a rewrite in TypeScript ([Which has growing and significant adoption, but as of 2019, 42.5% of JavaScript developers are unfamiliar with it or don't use it](https://2019.stateofjs.com/javascript-flavors/typescript))

## Drawbacks

There are several drawbacks to this approach:
1. TypeScript driven by JSDocs is a newer feature in TypeScript, not all TypeScript developers are familiar with the feature or it's syntax, there may be an additional learning curve.
2. Not all JavaScript developers are familiar with JSDoc, or with type annotations, there may be an additional learning curve.
3. It would require some refactoring, TypeScript discourages reassignment to a variable with different types (For example `foo` being a `number` the later a `string`). 

## Alternatives

1. Rewrite the code in TypeScript
2. Continue to maintain the types separate, but add a reminder in the PR template, and encourage maintainers to check types before merging changes

## Adoption strategy

> If we implement this proposal, how will existing unified developers adopt it?

Many unified packages have typings, for these packages, the typings would get more accurate.
For packages that previously did not have typings, typings would be natively provided.

> Is this a breaking change?

For packages which did not previously have typings, yes.
For packages with existing typings, this could be considered minor or even patch.

> Can we write a codemod?

Maybe, <https://medium.com/fhinkel/runtime-type-information-for-javascript-b134faac3c0a> (<https://github.com/fhinkel/type-profile>) might be able to be used to extract full types from the source using the test suite as a runner.
Since the conversion from type profile to TypeScript doesn't exist today, and because some types may not be able to be directly converted (see drawback 3).

It may be easier to do some manual refactoring.

> Should we coordinate with other projects or libraries?

Potentially with:
* <https://github.com/Microsoft/TypeScript>
* <https://github.com/open-wc/open-wc> who have also taken the [TypeScript with JSDoc approach](https://dev.to/open-wc/generating-typescript-definition-files-from-javascript-5bp2), and also are using [Remark](https://github.com/open-wc/open-wc/tree/master/packages/mdjs)
* <https://github.com/BoostIO/Boostnote> another project with leverages both TypeScript and Remark, and has members who are also a part of the collective.
* <https://github.com/mdx-js/eslint-mdx> an MDX and collective project using Remark with TypeScript.

## Unresolved questions

None
