# Matching an HTML Tag with Regular Expressions (Regex).

Regular expressions are a powerful tool for parsing and manipulating text, and they can be particularly handy when dealing with HTML tags. In this guide, we'll dive into the intricacies of a regex pattern designed to match HTML tags. By breaking down each component, we'll provide a comprehensive understanding of how this regex works and how you can use it effectively.

## Summary

In this guide, we'll dissect the following regex pattern that matches HTML tags:

```regex
/^<([a-z]+)([^<]+)*(?:>(.*)<\/\1>|\s+\/>)$/
```

This regex is used to identify and extract content from both opening and self-closing HTML tags. Let's explore each part of this pattern to understand its functionality.

## Table of Contents

- [Anchors](#anchors)
- [Tag Name](#tag-name)
- [Attributes](#attributes)
- [Tag Content](#tag-content)
- [Closing Tag](#closing-tag)
- [Self-Closing Tag](#self-closing-tag)
- [Putting It All Together](#putting-it-all-together)
- [Author](#author)

## Regex Components

### Anchors

The pattern starts with `^` and ends with `$`, which are anchors that ensure the entire string matches the regex pattern from start to finish.

### Tag Name

- `<([a-z]+)`: This part captures the tag name within angle brackets. The `[a-z]+` captures one or more lowercase letters, representing the tag name.

### Attributes

- `([^<]+)*`: This part captures any attributes within the tag. `[^<]+` matches one or more characters that are not angle brackets. The `*` quantifier allows for zero or more occurrences of attributes.

### Tag Content

- `(?:>(.*)<\/\1>|\s+\/>)`: This complex part handles both tag content and self-closing tags.
  - If the tag is not self-closing:
    - `>(.*)<\/\1>`: The `>` matches the closing of the opening tag. `(.*)` captures the content between the opening and closing tags. `<\/\1>` ensures that the corresponding closing tag matches the opening tag captured earlier.
  - If the tag is self-closing:
    - `\s+\/>`: `\s+` matches one or more whitespace characters, and `\/>` matches the self-closing tag.

### Closing Tag

The closing tag component, `<\/\1>`, ensures that the correct closing tag matches the opening tag captured earlier.

### Self-Closing Tag

The self-closing tag component, `\s+\/>`, allows the pattern to match tags that close themselves.

### Putting It All Together

By combining these components, the regex pattern can accurately identify and capture information from both opening and self-closing HTML tags.

## Author

This guide was written by Heidy Rivera, an enthusiastic web developer passionate about simplifying complex concepts. You can find my projects on [GitHub](https://github.com/HeiRiv).

