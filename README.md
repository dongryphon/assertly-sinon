# assertly-sinon
An [assertly](https://github.com/dongryphon/assertly)
([npm](https://www.npmjs.com/package/assertly)) add-on
[package](https://www.npmjs.com/package/assertly-sinon) for
[sinon](https://github.com/sinonjs/sinon) ([npm](https://www.npmjs.com/package/sinon)).

[![Build Status](https://travis-ci.org/dongryphon/assertly-sinon.svg?branch=master)](https://travis-ci.org/dongryphon/assertly-sinon)
[![Dependencies Status](https://david-dm.org/dongryphon/assertly-sinon/status.svg)](https://david-dm.org/dongryphon/assertly-sinon)
[![npm version](https://badge.fury.io/js/assertly-sinon.svg)](https://badge.fury.io/js/assertly-sinon)
[![MIT Licence](https://badges.frapsoft.com/os/mit/mit.svg?v=103)](https://opensource.org/licenses/mit-license.php)

If you are using sinon, this module expands Assertly with new words specific to testing
spy and spyCall objects created by sinon. For example:

    expect(spy).to.always.return(42);

# Installation

To install using `npm`:

    $ npm install assertly-sinon --save-dev

To install using `yarn`:

    $ yarn add assertly-sinon --dev

# Usage

To use this add-on, pass its `init()` method to `Assert.register()` like so:

    const Assert = require('assertly');
    const AssertlySinon = require('assertly-sinon');

    Assert.register(AssertlySinon.init);

## Improved Output (Optional)

By default, spys and spyCalls do not print cleanly using Node.js `inspect()` method. To
improve this, you can use `prettySpy`:

    let spy = AssertlySinon.prettySpy(sinon.spy(object, method));

The `prettySpy` method ensures that the spy and any spyCalls it returns from `getCall`
have a suitable `inspect()` method.

# API

The `sinon` API provides many kinds of helpers for spying and mocking. The API's
provided by this add-on are designed to make BDD-style assertions for sinon's spys
and spyCalls. To make it clear which sinon types work in specific contexts, the
names used for parameters are chosen to convey this as shown below:

 - `spy` - A spy created by `sinon.spy()`
 - `spyCall` - A call to a spy returned by `sinon.spy().getCall()`
 - `spyOrCall` - Either a `spy` or a `spyCall`

See these documents for the mapping of the sinon [Spy API](docs/spy.md) and
[Spy Call API](docs/spyCall.md).

## Assertions

 - [`call`](docs/words/call.md)
 - [`called`](docs/words/called.md)
 - [`calledOn`](docs/words/calledOn.md)
 - [`calledWith`](docs/words/calledWith.md)
 - [`return`](docs/words/return.md)
 - [`throw`](docs/words/throw.md)

## Properties

 - [`firstCall`](docs/words/firstCall.md)
 - [`secondCall`](docs/words/secondCall.md)
 - [`thirdCall`](docs/words/thirdCall.md)
 - [`lastCall`](docs/words/lastCall.md)

## Modifiers

This add-on adds new modifiers to Assertly.

### always

The `always` modifier is used by `return` and `throw` assertions when operating on
a spy.
