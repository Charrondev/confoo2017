## Remove The Boilerplate

## Tools

* ES6 / ES2015
* functional programming
* promises, async/await
* test helpers

### Functional Programming

#### partial application

Ex:
```
const path = require('path')
const first = path.join(__dirname, '../foo')
...
const second = path.join(__dirname, '../bar')
```

```
const relativePath = require('path')
    .join.bind(null, __dirname)
const first = relativePath('../foo')
...
const second = relativePath('../bar')
```

Designing function signatures

```
function fn(a, b, c) { ... }
const newFn = fn.bind(null, valueA, valueB)
newFn(valueC)
```

Tip: 
place on the on the left properties that will be known first

Ex.
```
// good, can be partially applied easily.
function updateUserInfo(userId, newInfo) { ... }

// bad
function updateUserInfo(info, userId) { ... }
```

Partial application from the left side is built into JS.

#### Partial application from the right

```
['1', '2', '3'].map(parseInt) // [1, NaN, NaN]

['1', '2', '3'].map((x) => {
    return parseInt(x, 10) //[1, 2, 3]
})
```

User libraries like lodash or [spots](https://github.com/bahmutov/spots) to partially apply from the right or from both sides.

[heroin](https://github.com/bahmutov/heroin) can be used to partially apply by name using dependency injection

#### Unary methods for chaining

```
function mul(a, b) {
    return a * b
}

const byK = mul.bind(undefined, constant)

```

#### Curried functions

Make any function unary. Found in helper libraries like lodash

#### Ramda libary

Puts callback first in map.

ex.
```
const R = require('ramda')

R.map(callback, array)

R.map (R.multiply(5), array)
```

#### Function composition
```
const computation = R.compose(printAll, multiplyAll)
// These are the same
printAll(multiplyAll(number))
computation(number)
```

R.pipe is like compose but puts things on different lines.

### Async code

In node callbacks are everywhere. Use promises or async/await

### Testing Code

* Choose a good test framework. Try Mocha, Jest
* Write a test wrapper or use one.
* Boilerplate for assertions. Try something like magix assert, Ava.
* A small performance penalty is worth it for shorter unit tests.

Ex. A good unit test

```
describe('something', () => {
    it('does this thing', () => {
        return get(url)
            .then(list => {
                // Where does this expected value come form
                // Maybe a json file saved from a previous time. Lots of boilerplate
                assert.equals(list, expected)
            })
    })
})
```

Jest solves this issue by automatically saving snapshots of previous test results. Ava has also added snapshot testing. bahmutov/snap-shot is a testing framework independant snapshot implementation.

Ex.
```
describe('something', () => {
    it('does this thing', () => {
        return get(url)
            .then(list => {
                assert(list).matchesSnapshot()
            })
    })
})
```

#### Dynamic Data?
```
const snapshot = require('snap-shot')
it('returns most populat item', () => {
    const top = api.getTopItem()
    snapshot(top)
})

Schema-shot is a potential solution, which will take a shot of the schema of what is returned, so it doesn't need to match as strongly.

### Conlusions

* Use small reusable functions
* Combine functions into pipelines
* Use promises or async / await
* Deal with boilerplate in your unit tests.