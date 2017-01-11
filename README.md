Markdown AST spec
=================

Working draft to design lossless AST for markdown. Unstable.

Use [issues tracker](https://github.com/markdown-it/markdown-ast-spec/issues)
to discuss.

**Goals & checkpoints**:

1. Allow support use cases, not available with current implementations. Examples:
    - Optimize editor highlight update after text change.
    - When user selects range at html page, provide range in source markdown doc.
    - Better sync scroll for previews.
2. Provide source mapping info.
3. Allow AST -> markdown write without formatting loss.
4. Performance:
    - Additional care should be applied to fast AST build/traverse in Javascript.
5. Analyse required operation and recommend minimal set of API functions.

---

Useful to read:

- [csstree](https://github.com/csstree/csstree) - interesting approach to fast
  tokenizer and other optimizations.
- [ESTree](https://github.com/estree/estree) - lossless JS AST design.
- [AST Explorer](http://astexplorer.net/) - explore different AST implementations.
