### One component is one element
There's no nested components encapsulated. No need to pass `nestedComponentProps`. You have direct access to any component that can be part of another one, such as `Popover.Arrow`.
```js { "showCode": true, "size": "80px" }
const { Block, Popover } = require('reas');

<Block relative>
  <Popover visible>
    <Popover.Arrow />
    Try to remove Popover.Arrow above.
  </Popover>
</Block>
```

### A component can be rendered [`as`](#as) any html element
This is useful when you want to render a `Button` as an anchor element, for example.
```js
const { Button } = require('reas');

<Button as="a" href="https://google.com" target="_Blank">Go to Google Website</Button>
```

### A component can be rendered [`as`](#as) any other React component
With that, you can render a `Button` as [`react-router`](https://reacttraining.com/react-router/)'s `Link`, for example. But, specially for `reas`, this is important so you can use [behaviors](#behaviors).
```js
const { Button, Flex } = require('reas');

<Button as={Flex}>Button</Button>
```

### A component can be rendered [`as`](#as) multiple other components
`Button` is `button`, `Flex` is `div`, but you can combine both and render it as a `span`.
```js
const { Button, Flex } = require('reas');

<Button as={[Flex, 'span']}>I'm a clickable/focusable span with display:flex</Button>
```

### A component can be [styled](#styling) with props
Just an alternative to `style={{ ... }}`.
```js
const { Button } = require('reas');

<Button relative backgroundColor="palevioletred" color="white">Button</Button>
```

### A component can be [styled](#styling) by extending another component
Using [styled-components](https://www.styled-components.com/).
```js
const { Button } = require('reas');

const StyledButton = Button.extend`
  position: relative;
  background-color: palevioletred;
  color: white;
`;

<StyledButton as="a" href="#button">Button</StyledButton>
```

### A `reas` component can be created by using [`as`](#as) enhancer
Take advantage of all above features in your components.
```js
const as = require('reas').default;

const enhance = as('span');
const Example = enhance(({ as: T, ...props }) => <T {...props} />);

<Example as="div" backgroundColor="palevioletred" color="white">Example</Example>
```

### A component state can be handled by using [state](#state) enhancers
State enhancers encapsulate the complexity behind state logic.
```js
const { Block, Button, Hidden, withHiddenState } = require('reas');

const enhance = withHiddenState();
const Example = enhance(({ hidden }) => (
  <Block>
    <Button onClick={hidden.toggle}>Toggle</Button>
    <Hidden visible={hidden.visible}>Hidden</Hidden>
  </Block>
));

<Example />
```

### A component API can be encapsulated by using [behavior](#behaviors) components
Behaviors such as `Hidden.Toggle` apply event handlers automatically.
```js
const { Block, Button, Hidden, withHiddenState } = require('reas');

const enhance = withHiddenState();
const Example = enhance(({ hidden }) => (
  <Block>
    <Button as={Hidden.Toggle} {...hidden}>Toggle</Button>
    <Hidden {...hidden}>Hidden</Hidden>
  </Block>
));

<Example />
```
