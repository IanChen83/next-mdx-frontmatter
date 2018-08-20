# next-mdx-frontmatter
Use [MDX](https://github.com/mdx-js/mdx) + [front-matter](https://github.com/jxson/front-matter) with [Next.js](https://github.com/zeit/next.js)

## Installation

`npm install --save next-mdx-frontmatter`

or

`yarn add next-mdx-frontmatter`

## Usage

Create a `next.config.js` in your project

```
// next.config.js
const withMdxFm = require('next-mdx-frontmatter')

let config = {}

// ...rest of your config

config = withMdxFm()(config) // Or withMdxMf(MdxFmOptions)(config)

module.exports = config
```

Then, all imported resources matching `.mdx` can be used as React components.

## Example

```
---
title: Example Page
description: Lorem ipsum dolor sit amet.
published: true
---

<div>

## Second Title

</div>
```

will be transformed into the following JSX (or something equivalent)

```
import React from 'react'

export default (
  <div>
    <h2>Second Title</h2>
  </div>
)

export const title = 'Example Page'
export const description = 'Lorem ipsum dolor sit amet.'
export const published = true
```

Then, this module can be used as

```
import Article, { title, description, published } from './article.mdx'

// rest of the application
```

### Options

* `extension` (**default:** `/\.mdx$/`): the file extension matched with the resource.
* `MDXOption` (**default:** `{}`): the options passed to [MDX options](https://github.com/mdx-js/mdx#options).

## License

MIT
