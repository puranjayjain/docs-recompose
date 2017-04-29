# mapProps

Replaces the current props with whatever the given function returns.

**Flow type:**

```js
type mapProps = (
  propsMapper: (ownerProps: Object) => Object
) => HigherOrderComponent
```

**PureScript type:**

```purescript
mapProps :: forall ownerProps props.
  (ownerProps -> props) -> HigherOrderComponent ownerProps props
```

## Examples

### Replacing props

```js
mapProps(props => {
  return {
    total: props.initialValue + props.change,
  }
})
```

**Incoming Props**

```js
{
  initialValue: 10,
  change: 5,
}
```

**Outgoing Props**

```js
{
  total: 15,
}
```
### Deriving other mappers

You can easily derive other mappers the same way you compose functions in functional programming:

```js
const omitProps = keys => mapProps(props => omit(keys, props))
```

If you're using Ramda or Lodash-FP, the following expression is equivalent because of currying:

```js
const omitProps = compose(mapProps, omit)
```