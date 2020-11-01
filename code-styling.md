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