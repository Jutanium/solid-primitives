# @solid-primitives/fullscreen

[![lerna](https://img.shields.io/badge/maintained%20with-lerna-cc00ff.svg)](https://lerna.js.org/)

Creates a primitive wrapper around the Fullscreen API that can either be used as a directive or a primitive.

## How to use it

```ts
const isActive: Accessor<boolean> = createFullscreen(
  ref: HTMLElement | undefined,
  active?: Accessor<FullscreenOptions | boolean>,
  options?: FullscreenOptions
);

// can be used as a directive

const MyComponent: Component = () => {
  const [fs, setFs] = createSignal(false);
  return (<div use:createFullScreen={fs} onClick={() => setFs(fs => !fs)}>
    {!fs() ? 'click to fullscreen' : 'click to exit fullscreen'}
  </div>);
}

// or a primitive

const MyComponent2: Component = () => {
  const [fs, setFs] = createSignal(false);
  let ref!: HTMLDivElement;
  const active: Accessor<boolean> = createFullscreen(ref, fs);
  return (<div ref={ref} onClick={() => setFs(fs => !fs)}>
    {!active() ? 'click to fullscreen' : 'click to exit fullscreen'}
  </div>);
}
```

You can either put the options into the second argument accessor output (useful for the directive use case) or as a third argument.

## Demo

TODO

## Changelog

<details>
<summary><b>Expand Changelog</b></summary>

0.0.100

Initial release

</details>
