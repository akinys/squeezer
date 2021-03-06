---
title: Development - Variables
---

Squeezer supports both global variables and stage variables.

After compiling the project variables can be accessed from `FUNCTION/src/.vars.json`

### Global variables

`PROJECT_DIR/squeezer.yml` :

```yaml
vars:
  foo: "bar"
```

On this case the `foo` variable will be globally available trough all functions and stages .

### Stage variables
`PROJECT_DIR/squeezer.yml` :

```yaml
vars:
  foo: "bar"
  stages:
    dev:
      foo: "bar - dev"
```

`sqz compile --stage dev`

Here we compiled the functions as `dev` stage , therefore the `foo` variable value will be **bar - dev**

### Environment variables

You can access terminal variables inside your template , eg: 

`$ export var1="test"`

`template.yml` :

```yaml
  var1: ${env.var1}
```

**RESULT**

```yaml
  var1: test
```

### Self variables

You can re-use variable from the current template

```yaml
a: 1
```

```yaml
b: ${this.a}
```

**RESULT**

```yaml
b: 1
```