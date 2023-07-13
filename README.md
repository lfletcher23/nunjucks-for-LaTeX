## nunjucks-for-LaTeX README

Syntax highlighting for a custom version of Nunjucks that's LaTeX compatible

### Nunjucks Configuration

```
const env = nunjucks.configure(your_dir, {
    autoescape: false,
    tags: {
        variableStart: '#!',
        variableEnd: '!#',
        blockStart: '[##',
        blockEnd: '##]',
        commentStart: '%!',
        commentEnd: '!%'
    }
});

env.addFilter('texscape', function(str: string) {
    const fixslash = str.replace(/\\/g, "\\textbackslash");
    const fixsymbols = fixslash.replace(/(\$|%|&|#|_|\{|\})/g, "\\$1"); // replace tex special characters
    const fixspecial = fixsymbols.replace(/(\^|~)/g, "\\$1\{\}") // replace tex special characters with a different replacement syntax
    return fixspecial;
});
```

### Supports these file extensions
```
.njk, .nunjucks

