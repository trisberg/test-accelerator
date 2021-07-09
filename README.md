# test-accelerator
Test Accelerator

### Run 0

> No accelerator.yaml

> Accelerator Log
```
Options

{
"projectName" : "test-accelerator",
"projectDescription" : ""
}

Log

┏ engine (Chain)
┃  Info Running Chain(Include, UniquePath)
┃ ┏ engine.transformations[0] (Include)
┃ ┃  Info Will include [**]
┃ ┃ Debug config/test-accelerator.yaml matched [**] -> included
┃ ┃ Debug README.md matched [**] -> included
┃ ┗ Debug LICENSE matched [**] -> included
┗ ╺ engine.transformations[1] (UniquePath)
```

### Run 1

> accelerator.yaml
```
engine:
  type: Include
  patterns: ["**"]
```

> Accelerator Log
```
Options

{
"projectName" : "test-accelerator",
"projectDescription" : ""
}

Log

┏ engine (Chain)
┃  Info Running Chain(Include, UniquePath)
┃ ┏ engine.transformations[0] (Include)
┃ ┃  Info Will include [**]
┃ ┃ Debug config/test-accelerator.yaml matched [**] -> included
┃ ┃ Debug README.md matched [**] -> included
┃ ┗ Debug LICENSE matched [**] -> included
┗ ╺ engine.transformations[1] (UniquePath)
```

### Run 2

> accelerator.yaml
```
engine:
  includes: [ "**" ]
```

> Accelerator Log
```
Options

{
"projectName" : "test-accelerator",
"projectDescription" : ""
}

Log

┏ engine (Chain)
┃  Info Running Chain(Mega, UniquePath)
┃ ┏ engine.transformations[0] (Mega)
┃ ┃  Info Mega running as Include
┃ ┃ engine.transformations[0].includes (Include)
┃ ┃  Info Will include [**]
┃ ┃ Debug config/test-accelerator.yaml matched [**] -> included
┃ ┃ Debug README.md matched [**] -> included
┃ ┗ Debug LICENSE matched [**] -> included
┗ ╺ engine.transformations[1] (UniquePath)
```

### Run 3

> accelerator.yaml
```
engine:
  includes: ["**"]
  excludes: ["config/**"]
```

> Accelerator Log
```
Options

{
"projectName" : "test-accelerator",
"projectDescription" : ""
}

Log

┏ engine (Chain)
┃  Info Running Chain(Mega, UniquePath)
┃ ┏ engine.transformations[0] (Mega)
┃ ┃  Info Mega running as Chain(Include, Exclude)
┃ ┃ engine.transformations[0].<mega> (Chain)
┃ ┃  Info Running Chain(Include, Exclude)
┃ ┃ ┏ engine.transformations[0].<mega>.transformations[0] (Include)
┃ ┃ ┃  Info Will include [**]
┃ ┃ ┃ Debug config/test-accelerator.yaml matched [**] -> included
┃ ┃ ┃ Debug README.md matched [**] -> included
┃ ┃ ┗ Debug LICENSE matched [**] -> included
┃ ┃ ┏ engine.transformations[0].<mega>.transformations[1] (Exclude)
┃ ┃ ┃  Info Will exclude [config/**]
┃ ┃ ┃ Debug config/test-accelerator.yaml matched [config/**] -> excluded
┃ ┃ ┃ Debug README.md didn't match [config/**] -> included
┃ ┗ ┗ Debug LICENSE didn't match [config/**] -> included
┗ ╺ engine.transformations[1] (UniquePath)
```

### Run 4

> accelerator.yaml
```
engine:
  excludes: ["config/**"]
  includes: ["**"]
```

> Accelerator Log
```
Options

{
"projectName" : "test-accelerator",
"projectDescription" : ""
}

Log

┏ engine (Chain)
┃  Info Running Chain(Mega, UniquePath)
┃ ┏ engine.transformations[0] (Mega)
┃ ┃  Info Mega running as Chain(Include, Exclude)
┃ ┃ engine.transformations[0].<mega> (Chain)
┃ ┃  Info Running Chain(Include, Exclude)
┃ ┃ ┏ engine.transformations[0].<mega>.transformations[0] (Include)
┃ ┃ ┃  Info Will include [**]
┃ ┃ ┃ Debug config/test-accelerator.yaml matched [**] -> included
┃ ┃ ┃ Debug README.md matched [**] -> included
┃ ┃ ┗ Debug LICENSE matched [**] -> included
┃ ┃ ┏ engine.transformations[0].<mega>.transformations[1] (Exclude)
┃ ┃ ┃  Info Will exclude [config/**]
┃ ┃ ┃ Debug config/test-accelerator.yaml matched [config/**] -> excluded
┃ ┃ ┃ Debug README.md didn't match [config/**] -> included
┃ ┗ ┗ Debug LICENSE didn't match [config/**] -> included
┗ ╺ engine.transformations[1] (UniquePath)
```

### Run 5

> accelerator.yaml
```
engine:
  type: Chain
  transformations:
    - type: Exclude
      patterns: ["config/**"]
    - type: Include 
      patterns: ["**"]
```

> Accelerator Log
```
Options

{
"projectName" : "test-accelerator",
"projectDescription" : ""
}

Log

┏ engine (Chain)
┃  Info Running Chain(Chain, UniquePath)
┃ ┏ engine.transformations[0] (Chain)
┃ ┃  Info Running Chain(Exclude, Include)
┃ ┃ ┏ engine.transformations[0].transformations[0] (Exclude)
┃ ┃ ┃  Info Will exclude [config/**]
┃ ┃ ┃ Debug config/test-accelerator.yaml matched [config/**] -> excluded
┃ ┃ ┃ Debug README.md didn't match [config/**] -> included
┃ ┃ ┗ Debug LICENSE didn't match [config/**] -> included
┃ ┃ ┏ engine.transformations[0].transformations[1] (Include)
┃ ┃ ┃  Info Will include [**]
┃ ┃ ┃ Debug README.md matched [**] -> included
┃ ┗ ┗ Debug LICENSE matched [**] -> included
┗ ╺ engine.transformations[1] (UniquePath)
```

### Run ?

> accelerator.yaml
```
```

> Accelerator Log
```
```

### Run ?

> accelerator.yaml
```
```

> Accelerator Log
```
```

### Run ?

> accelerator.yaml
```
```

> Accelerator Log
```
```

### Run ?

> accelerator.yaml
```
```

> Accelerator Log
```
```

### Run ?

> accelerator.yaml
```
```

> Accelerator Log
```
```
