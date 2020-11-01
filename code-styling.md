# Code styling document for IDI UI UX team

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
In this exmaple we can clearly see how we can sort properties by groups,
For example margin + padding, width + height

.css-block {
    margin: 0 auto;
    padding: 5px;
    width: 100px;
    height: 50px;
    border-bottom: 1px;
}
```

