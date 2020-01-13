# react-navigation-collapsible

[![npm](https://img.shields.io/npm/v/react-navigation-collapsible/next.svg)](https://www.npmjs.com/package/react-navigation-collapsible) [![npm](https://img.shields.io/npm/dm/react-navigation-collapsible.svg)](https://www.npmjs.com/package/react-navigation-collapsible) [![code style: prettier](https://img.shields.io/badge/code_style-prettier-ff69b4.svg)](https://github.com/prettier/prettier)

An extension of react-navigation that makes your header collapsible.

Try out on [Expo Snack](https://snack.expo.io/@benevbright/react-navigation-collapsible)

## Compatibility 🚧

| `react-navigation` | `react-navigation-collapsible` | Documentation                                                                        |
| ------------------ | ------------------------------ | ------------------------------------------------------------------------------------ |
| ^5.0.0 (`next`)    | ^5.0.0 (`next`)                | current                                                                              |
| ^4.0.0 (`latest`)  | ^3.0.0 (`latest`)              | [v3-4 branch](https://github.com/benevbright/react-navigation-collapsible/tree/v3-4) |
| ^2.0.0             | ^2.0.0                         | [v2 branch](https://github.com/benevbright/react-navigation-collapsible/tree/v2)     |

The navigation tab is no longer supported due to the [Android bug from react-native](https://github.com/facebook/react-native/issues/21801).

## Usage

### For Regular Stack Header

<img src="https://github.com/benevbright/react-navigation-collapsible/blob/v5/docs/demo-sample1.gif?raw=true">

```js
import { CollapsibleStack } from 'react-navigation-collapsible';

function App() {
  return (
    <NavigationNativeContainer>
      <Stack.Navigator>
        /* Wrap your Stack.Screen */
        {CollapsibleStack(
          <Stack.Screen
            name="HomeScreen"
            component={MyScreen}
            options={{
              headerStyle: { backgroundColor: 'green' },
              title: 'Home',
            }}
          />,
          {
            collapsedColor: 'red',
          }
        )}
      </Stack.Navigator>
    </NavigationNativeContainer>
  );
}
```

```js
import { Animated } from 'react-native';
import { useCollapsibleStack } from 'react-navigation-collapsible';

const MyScreen = ({ navigation, route }) => {
  const {
    onScroll /* Event handler */,
    containerPaddingTop /* number */,
    scrollIndicatorInsetTop /* number */,
    /* Animated.AnimatedInterpolation by scrolling */
    translateY /* 0.0 ~ -headerHeight */,
    progress /* 0.0 ~ 1.0 */,
    opacity /* 1.0 ~ 0.0 */,
  } = useCollapsibleStack();

  return (
    <Animated.FlatList
      onScroll={onScroll}
      contentContainerStyle={{ paddingTop: containerPaddingTop }}
      scrollIndicatorInsets={{ top: scrollIndicatorInsetTop }}
      /* rest of your stuff */
    />
  );
};
```

See [/example/App.tsx](https://github.com/benevbright/react-navigation-collapsible/tree/master/example/App.tsx) and [/example/src/S1-RegularHeaderScreen.tsx](https://github.com/benevbright/react-navigation-collapsible/tree/master/example/src/S1-RegularHeaderScreen.tsx)

## Install

```bash
# install module
yarn add react-navigation-collapsible@next
```

## Contribution

PR is welcome!

### Testing your library code with the example

[/example](https://github.com/benevbright/react-navigation-collapsible/tree/master/example) imports the library directly from the root folder, configured with [babel-plugin-module-resolver](https://github.com/benevbright/react-navigation-collapsible/tree/master/example/babel.config.js#L10).
So, just turn the `watch` option on at the root folder while you're making changes on the library, and check them on the example.

```bash
yarn tsc -w
```
