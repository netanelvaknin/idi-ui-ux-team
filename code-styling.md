# Code styling document for IDI UI UX team
&nbsp;
&nbsp;
&nbsp;
&nbsp;
&nbsp;
## CSS
### 1. Ordering by groups
#### Bad:
Ordering css properties by group types
```
.css-block {
    margin: 0 auto;
    width: 100px;
    padding: 5px;
    border-bottom: 1px;
    height: 50px;
}
```

#### Good:
```
/* In this exmaple we can clearly see how we can sort properties by groups,
For example margin + padding, width + height */

.css-block {
    margin: 0 auto;
    padding: 5px;
    width: 100px;
    height: 50px;
    border-bottom: 1px;
}
```

### 2. One line CSS property
#### Bad:
```
.css-block {
    width: 100px;
}
```

### Good:
```
/* Instead - one line. This simple action will significantly decrease the amount of lines in our code and will be more readable*/
.css-block { width: 100px; }
```

### 3. Selector ordering
Selectors need to ordered by their specificity and grouped by similarity. This ensures code is easy to find and change later in the process. 
#### Bad:
```
form {
    ...
}

form label span {
    ...
}

form label {
    ...
}
```

#### Good: 
```
form {
    ...
}

form label {
    ...
}

form label span {
    ...
}
```


### 3. Selector nesting
Selectors nesting will be not over 3 levels of deep
#### Bad:
```
.wrapper { // 1
    div { // 2
        span { // 3
            a { color: red; } //4 
        }
    }
}
```
#### Good:
```
.wrapper { // 1
    span  { // 2
        a {color: red;} // 3
    }
}
```

&nbsp;
&nbsp;
&nbsp;
&nbsp;
&nbsp;
## Styled Components
### 1. Avoiding from tag selectors
In styled components we should be avoid as much as possible from select nested elements with their tag name. This can cause future bugs when other developers will change the components markups.
#### Bad:
```
const ExampleComponent = styled.div`
    div:nth-child(2) {} // Should be avoided
`;
```

#### Good:
```
// Better option (If possible)
const ExampleComponent = styled.div`
    .top-bar {}
`;
```
&nbsp;
&nbsp;
&nbsp;
&nbsp;
&nbsp;
## React
### 1. Ordering props
Props that start with the word "on" will allways be in the *END* of the interface / props destructuring order.
This will make more sence because we are dividing them to two parts: inputs / outputs (handlers).
#### Bad:
```
interface ComponentProps {
    onChange: (e) => void;
    value: string;
    label: string;
    error: boolean;
}
```

#### Good:
```
interface ComponentProps {
    value: string;
    label: string;
    error: boolean;
    onChange: (e) => void;
}
```
