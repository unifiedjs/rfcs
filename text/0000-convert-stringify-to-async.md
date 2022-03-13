*   Start date: 2022-03-13
*   Scope: unifiedjs/unified-engine
*   RFC PR: <!-- leave this empty -->
*   Implementation issue(s): <!-- leave this empty -->

# Summary

Update the `stringify` function to be an async function.

## Motivation

Why are we doing this?
The change allows for great fexibliy in implementing Compile plugins, by allowing `stringify`
to return a promise.
What use cases does it support?
Cases when Compile is naturally async.
What is the expected outcome?

Currently all implementations of Compile plugins must be sync, this is becasuse `stringify`
is async and the results of the Complie plugin is used before internally in `stringify`.
`unified-engine` uses `trough` to call `stringify`, `trough` implicitly handles middle-ware
functions returning values or promises. Hence, updating `stringify` have no side effects since
`trough` will resolve the promise before calling the next middle-ware.

## Detailed design

* update `lib/file-pipeline/stringify.js` to be async
* update `value = context.processor.stringify(context.tree, file)` to `value = await context.processor.stringify(context.tree, file)`

## Drawbacks

Why should we *not* do this?
Please consider:

No clear drawbacks,

There are tradeoffs to choosing any path.
Attempt to identify them here.

## Alternatives

What other designs have been considered?
Could update the processing pipeline from
`.use(chunk(trough().use(stringify).use(copy).use(stdout).use(fileSystem)))` to
`.use(chunk(trough().use(stringify).use(setResult).use(copy).use(stdout).use(fileSystem)))`
* update stringify to return a `string | Buffer | undefined | Promise<string | Buffer | undefined>`
* update stringify to not set `file.value` or `file.result` move that code to `setResult`
What is the impact of not doing this?
This is a larger change and has no obvious benefits over the main solution.

## Adoption strategy

If we implement this proposal, how will existing unified developers adopt it?

* It will be transparent to all unified developers, expect does developing Compile plugins

Is this a breaking change? `No  `

Can we write a codemod?
 `No need `

Should we coordinate with other projects or libraries?  `No need`

## Unresolved questions

No obvious unresolved questions.
