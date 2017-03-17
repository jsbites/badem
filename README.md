## Unmaintained Software

I’m not planning to contribute to this project for a while.

If you are interested in being a contributor, [please let me know](mailto:volkan.io).

Thanks,

Volkan.

----



```
  ______    ______    _____    ______    __    __
 /\  == \  /\  __ \  /\  __-. /\  ___\  /\ "-./  \
 \ \  __<  \ \  __ \ \ \ \/\ \\ \  __\  \ \ \-./\ \
  \ \_____\ \ \_\ \_\ \ \____- \ \_____\ \ \_\ \ \_\
   \/_____/  \/_/\/_/  \/____/  \/_____/  \/_/  \/_/
```

`badem` is an abstract component composer that does not require a DOM.

## Alpha-Stage Software Warning

> `badem` is in its early stages; so anything in its implementation can change.
>
> Until it hits `version 1.0`, I’ll be liberally introducing breaking changes, please keep that in mind and **fix your versions in your package.json** if you depend on `badem` in your apps.
>
> Once `badem` hits `version 1.0`, its API will stabilize, and the changes will be more backwards-compatible, as I will follow the [Semantic Versioning 2.0.0](http://semver.org/spec/v2.0.0.html) standards.

## About This Repository

This repository is a part of the [Byte-Sized JavaScript VideoCasts][vidcast].

```
  _               __
 |_)   _|_  _ __ (_  o _   _   _|
 |_) \/ |_ (/_   __) | /_ (/__(_|
     /        |  _.     _. (_   _ ._ o ._ _|_
            \_| (_| \/ (_| __) (_ |  | |_) |_
                                       |
            »»  bytesized.tv  ««
```

## Byte-Sized What?!

[Byte-Sized JavaScript][vidcast].

It is a compilation of short (*around ten minutes*) monthly screencasts about **JavaScript** and related technologies.

[vidcast]: https://bytesized.tv/ "ByteSized.TV"

## About `badem`

`badem` started as a thought experiment:

> “What if you have to create components in an extremely-restricted environment where there is no DOM or `window`?”

In that kind of an environment, you have to create a **higher-order** mounter, that just creates a tree-like hierarchy and **delegates** the actual instantiation and initialization of the components “elsewhere” \[1\].

\[1\]: “elsewhere” can be anything: A custom TV operating system, an IOC, a native application, a “Façade” to actual real-life components, like a robot’s arm.

## Great Theory — Are There Any Practical Implementations?

Currently, I’m experimenting how to integrate `badem` to [smartface.io](https://smartface.io), so that you can render a **smartface.io** UI just by tracing a JSON descriptor.

Defining how the UI will render and behave declaratively in a **JSON** file opens on many possibilities.

One of these possibilities is the ability to integrate a custom WYSIWYG designer to the code:

So the designer will generate a **JSON** instead of a large **code-behind** autogenerated code.

This approach has several advantages:

* The footprint of the generated **JSON** is much smaller.
* **JSON** is much declarative than your standard *code-behind* IDE code: **MUCH** easier to read and understand.
* **JSON** is smaller in size, easier, and faster to generate.
* You can serialize/deserialize a **JSON**, and it will reflect the same state across the boundaries of your system; you cannot do the same with an IDE-generated code, so parts of it might get “lost in translation” — Code is not serializable; data is.
* The typical designer output is generally some form of an XML or JSON already; so it is much easier to convert it to a `badem`-compatible **JSON**.
* The generation process is be less error-prone (see the “serialization” point above) — There are more edge cases when you generate actual source code: you can create invalid, or incomplete source code, you can have syntax errors, or logic errors that are hard to see)
* Since `badem` JSON is an almost identical representation of the UI, it is a lot easier to spot out bugs and regressions.
* Related to the above topic: Testing **JSON** is much easier than testing code: Once you create a proper schema-validator, you are almost there — no need to stub, or mock anything, because everything is **declarative**.

This declarative programming is **User Interface as Code**, which is (*much better and*) diagonally different from a “user-interface-generated code”.

## Installation

Install using **NPM**:

```bash
npm install badem --save
```

## The `dist` Folder

There are different `badem` distributions for various environments:

* Use `require( 'badem/dist/nodejs' )` in a **Node.JS** environment.
* Use `require( 'badem/dist/js' )` to be used in a **JavaScript** (ES6+) environment.

I will add more distribution formats later.

## Usage Examples

Here’s how you mount components with `badem`:

```js
const log = console.log;

// Using the Node.JS distribution:
const mount = require( 'badem/dist/nodejs' ).mount;

const store = require( './store' );
const app = require( './app.json' );

mount( store, app )
    .then( () => log( 'All should have been done by now!' ) )
    .catch( () => log( 'Oh poop!' ) );
```

See the `./examples` folders for additional details and usage examples.

## Dependencies

For development, you’ll need a recent version of [Node.JS](https://nodejs.org) and [NPM](https://npmjs.org).

[The current stable Node.JS version](https://nodejs.org/en/) is recommended.

`badem` is self-sufficient. — For production use, you just need a good-enough JavaScript runtime.

## Package Scripts

Here are the helper npm scripts that you can run via `npm`:

* `npm test`: Executes the unit tests.
* `npm run lint`: Checks whether the source JavaScript is well-formed.
* `npm run build:node`: Generate a **Node.JS** distribution inside the `./dist` folder.
* `npm run build:js`: Generate a **JavaScript** (ES6+) distribution inside the `./dist` folder.
* `npm run build`: Executes all of the `build:*` actions.

## Important Files and Folders

* `src`: The source files live here.
* `dist`: Once you run the build script, distribution bundles will be placed here.
* `bin`: Scripts that are mostly used by `npm`.
* `CHANGELOG.md`: A log of what has been done since the last version.
* `CODE_OF_CONDUCT.md`: Tells the collaborators to be nice to each other.
* `README.md`: This very file.
* `.babelrc`: Used for development; configures `babel`.
* `.eslintrc`: Used for development; configures `eslint`.
* `.travis.yml`: Used for CI; configures Travis.
* `webpack.node.config.js`: Helps `webpack` to bundle a **Node.JS** distribution inside the `./dist` folder.

## Wanna Help?

Any help is more than appreciated.

If you want to contribute to the source code, **fork this repository** and **create a pull request**.

> In lieu of a formal style guide, take care to maintain the existing coding style.

Also, don’t forget to add unit tests for any new or changed functionality.

If you want to report a bug; or share a comment or suggestion, [file an issue](https://github.com/jsbites/badem/issues/new).

## I’ve Found a Bug; I Have an Idea

[For bug reports and suggestions, please file an issue](https://github.com/jsbites/badem/issues/new).

## Contact Information

* **Project Maintainer**: [Volkan Özçelik](https://volkan.io/)
* **Project Website**: [bytesized.tv](https://bytesized.tv/)

## License

MIT-licensed. — [See the license file for details](LICENSE.md).

## Code of Conduct

We are committed to making participation in this project a harassment-free experience for everyone, regardless of the level of experience, gender, gender identity and expression, sexual orientation, disability, personal appearance, body size, race, ethnicity, age, religion, or nationality.

[See the code of conduct for details](CODE_OF_CONDUCT.md).
