<p align="center">
  <br /><br />
  <img src="logo/logo-vertical.png" alt="reas" height="150" />
  <br /><br /><br />

  <a href="https://github.com/diegohaz/nod">
    <img 
      alt="Generated with nod"
      src="https://img.shields.io/badge/generator-nod-2196F3.svg?style=flat-square" 
    />
  </a>

  <a href="https://npmjs.org/package/reas">
    <img 
      alt="NPM version"
      src="https://img.shields.io/npm/v/reas.svg?style=flat-square" 
    />
  </a>

  <a href="https://travis-ci.org/diegohaz/reas">
    <img
      alt="Build Status"
      src="https://img.shields.io/travis/diegohaz/reas/master.svg?style=flat-square" 
    />
  </a>

  <a href="https://codecov.io/gh/diegohaz/reas/branch/master">
    <img 
      alt="Coverage Status"
      src="https://img.shields.io/codecov/c/github/diegohaz/reas/master.svg?style=flat-square" 
    />
  </a>
  <br /><br />
</p>

A minimalist and highly customizable component system built on top of [React](https://reactjs.org) and [styled-components](https://www.styled-components.com).

- [**Documentation**](https://diegohaz.github.io/reas/)
- [**Components**](https://diegohaz.github.io/reas/#components)

## Install

Yarn:
```sh
yarn add reas
```

npm:
```sh
npm install --save reas
```

## Example

<p align="center">
  <img 
    src="https://user-images.githubusercontent.com/3068563/35465289-0cb7fe96-02e2-11e8-8bc5-60abcb6e92ac.gif"
    width="200" 
  />
</p>

Play with it on [CodeSandbox](https://codesandbox.io/s/m4n32vjkoj) or go to [Documentation](https://reas.js.org) for more examples.

```jsx
import React from 'react'
import { render } from 'react-dom'
import { InlineBlock, Button, Popover, Backdrop, Shadow, withPopoverState } from 'reas'

const TransparentBackdrop = Backdrop.as(Popover.Hide).extend`
  background-color: transparent;
`

const App = withPopoverState(({ popover }) => (
  <InlineBlock relative>
    <Button as={Popover.Toggle} {...popover}>Toggle</Button>
    <TransparentBackdrop {...popover} />
    <Popover {...popover}>
      <Popover.Arrow />
      <Shadow depth={4} />
      Popover
    </Popover>
  </InlineBlock>
))

render(<App />, document.getElementById('root'))
```

## License

MIT © [Diego Haz](https://github.com/diegohaz)
