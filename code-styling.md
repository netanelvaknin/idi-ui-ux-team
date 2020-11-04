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
.wrapper { /* 1 */
    div { /* 2 */
        span { /* 3 */
            a { color: red; } /* 4 */ 
        }
    }
}
```
#### Good:
```
.wrapper { /* 1 */
    span  { /* 2 */
        a {color: red;} /* 3 MAXIMUM! */
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


### 2. Single condition instead of repeating conditions
In our styled components we have direct access to theme.brand. There is no need to repeat our conditions in every property.
Instead we can just declare one Ternary condition inside the component.
#### Bad:
```
const ExampleComponent = styled.div`
    font-family: ${props => props.theme.fontBold};
    font-size: ${props => props.theme.brand.is9m() ? '1.8rem' : '2.2rem'};
	background-color: ${props => props.theme.brand.is9m() ? 'transparent': 'rgba(247, 249, 249, 1)'};
	color: ${props => props.theme.brand.is9m() && props.theme.palette.secondary.main};
`;
```
#### Good:
```
const ExampleComponent = styled.div`
    // Common properties (for all brands) is outside the condition allways
    font-family: ${props => props.theme.fontBold};
    ${props => props.theme.brand.is9m() ? ` // 9m block
        font-size: 1.8rem;
        background-color: transparent;
        color: {props.theme.palette.secondary.main};
    ` : ` // other brands block
        font-size: 2.2rem;
        background-color: rgba(247, 249, 249, 1);
    `}
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
