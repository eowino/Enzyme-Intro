# Enzyme

### What is it?

A test utility library written by AirBnB. It simplifies the testing of React components.

### What can it do?

It allows you to target 3 test cases:
* Testing your components in isolation
* Testing the lifecycle functions of your components
* Testing the rendered HTML of your components

### What is the API like?

Enzyme provides a jQuery like API for manipulation and traversal

### How to install

> **Note:**
> - Assuming you have Node and NPM installed
> - Enzyme has a dependency on React-Addons-Test-Utils

In the terminal: `npm install enzyme react-addons-test-utils --save-dev`

### Useful API Features

#### Shallow Rendering
Useful for testing components in isolation without worrying about side effects produced
by any of its child components.

The `shallow` function returns a shallow wrapper object that allows you to query the
rendered output.

#### Mount
Used for full DOM  rendering. 

`mount` is useful for testing components with lifecycle events or that interact with
DOM APIs. You can either run your tests inside a browser or utilise a library called
JS DOM to implement a headless browser in JS.

To install JS DOM run: `npm install --save-dev jsdom`

The usage of `mount` API is fairly similar to the `shallow` API. Instead of working
with the `shallow` wrapper, you work with the React wrapper.

To test lifecycle events, consider using a library called Sinon. It allows you to create
spies, stubs, or marks. Spies allow you to "spy" on lifecycle events and validate that
they fired.

To install run: `npm install --save-dev sinon`

#### Render
The `render` API allows you to test the static HTML that components render. 

### When to use either of these API?
Use the `shallow` API by default. It accomodates the majority of test cases that you may want to test against.

When you have a component and want to use it's life cycle events, use `mount`.

If you want to test a component that gets rendered on the server, or a component
that simply returns HTML i.e. no nested components in it, consider using `render`.

### Tips
When your tests are failing and wish to debug, consider using the `debug()` function which returns a String representation of your component.

Example usage:
`const wrapper = mount(<MyComponentName />);
 console.log(wrapper.debug())
`

Other options include:
* adding the `--debug` flag in your package.json on your scripts.test. This will allow you to use debugger statement within your test and have the debugger stop on those lines. This option will allow you to interact with the debugger from the command line.

* node-interceptor allows you to to use the Chrome Dev Tools