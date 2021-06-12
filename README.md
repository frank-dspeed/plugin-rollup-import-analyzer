# plugin-rollup-import-analyzer
This Plugin is not Created to be used in the bundling process it self it is created to get used with rollup to create a AST of dependencies and the supported module types





## Usage
```
rollup -c analyze.bundle.js
```

creates analyze.bundle.ast.js

## Content
Example dependies
```
import My 'xxxx/xxxx' // Without extension and not relativ path so a job for resolve
import my 'package' // Without extension and not relativ needs resolve
import my './no' // without extension and relative needs resolve of extension including many diffrent resolve algos

```

## Output
Will contain FilePath, UniqRef, Content, 

The Output is also designed to Stay Cached. As This is a dev tool we incremental Modify the result as we 
never expect to get the result that we want as also to save computation and catch changes.
```
const AnalyzedDependencieAsts = {
  esm: {}
  cjs: {}
  umd: {}
  amd: {}
  npm: {
    conditions: {
      "import"
      "require"
    }
  }
  pnp: {}
  customResolveViaAnalyzerPlugin: {}
}
```

Methods used with the AnalyzedDepAst
```
resloveNextWith(esm, pluginFunction) // Extends the ast with new information
```
