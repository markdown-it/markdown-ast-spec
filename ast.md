Markdown-it AST spec
====================

Methods
-------

- `clone(AST)`
- `walk(AST, handler)`
- `toJSON()`

TODO (or check possibility):

- walk inlines
- walk blocks (+ deepness?)
- partial text node replace
  - by text
  - by nodes (linkify, for example)
- parse
- from JSON
- to HTML


Nodes
-----

### Abstract node

Fields:

- `type`
- `children` - childrens list if available

TODO:

- sourcemap data
- optimize traverse
- check required transforms and optimize those

### Blockquote

```
> foo **bar
>baz**
cad
```

=>

```js
{
  type: 'document',
  children: [
    {
      type: 'blockquote',
      children: [
        type: 'p',
        children: [
          type: 'inline'
          children: [
            {
              type: 'indent',
              value: '> '
            }
            {
              type: 'text',
              value: 'foo '
            }
            {
              type: 'bold',
              marker: '**'
              children: [
                {
                  type: 'text',
                  value: 'bar'
                }
                {
                  type: 'softbreak',
                  value: '\n'
                },
                {
                  type: 'indent',
                  value: '>'
                }
                {
                  type: 'text',
                  value: 'bad'
                }
                {
                  type: 'softbreak',
                  value: '\n'
                },
                {
                  type: 'text',
                  value: 'cad'
                }
              ]
            }
          ]
        ]
      ]      
    }
  ]
}
```


# List

```
-  foo
 - bar
baz
```

=>

```js
{
  type: 'document',
  kind: 'block'
  children: [
    {
      type: 'ul',
      children: [
        {
          type: 'li',
          marker: '-'
          children: [
            {
              type: 'inline',
              children: [
                {
                  type: 'indent',
                  value: '- '
                }
                {
                  type: 'text',
                  value: 'foo'
                }                
                {
                  type: 'softbreak',
                  value: '\n'
                },
              ]
            }
          ],
        },
        {
          type: 'li',
          marker: '-'
          children: [
            {
              type: 'inline',
              children: [
                {
                  type: 'indent',
                  value: ' - '
                }
                {
                  type: 'text',
                  value: 'bar'
                }                
                {
                  type: 'br',
                  soft: true,
                  value: '\n'
                },
                {
                  type: 'text',
                  value: 'baz'
                }                
              ]
            }
          ],
        }
      ]
    }
  ]
}
```
