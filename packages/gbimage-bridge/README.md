<h1 align="center">
  g(atsby-background-)image-bridge
</h1>
<p align="center">
  <i>Bringing gatsby-background-image to Gatsby 3!</i>
</p>
<p align="center">
  <a href="https://github.com/timhagn/gatsby-background-image/blob/main/LICENSE">
    <img src="https://img.shields.io/badge/license-MIT-blue.svg" alt="gatsby-background-image-es5 is released under the MIT license." />
  </a>
  <a href="https://www.npmjs.org/package/gbimage-bridge">
    <img src="https://img.shields.io/npm/v/gbimage-bridge.svg" alt="Current npm package version." />
  </a>
</p>

`g(atsby-background-)image-bridge` bridges the gap between the new
`gatsby-plugin-image` syntax of providing images and the old
`fluid / fixed` syntax currently still used by
[`gatsby-background-image`](https://github.com/timhagn/gatsby-background-image)
& the now deprecated `gatsby-image`.

Don't know what I'm talking about? Head over to
[Migrating from gatsby-image to gatsby-plugin-image](https://www.gatsbyjs.com/docs/reference/release-notes/image-migration-guide/)
to see for yourself what changed in Gatsby 3 under the hood!

## Table of Contents

- [Install](#install)
- [How to Use](#how-to-use)
- [Why this package](#why)

## Install

To add `gbimage-bridge` as a dependency to your Gatsby-project use

```bash
yarn add gbimage-bridge
```

or

```bash
npm install --save gbimage-bridge
```

You will need `gatsby-background-image` & have `gatsby-plugin-image` installed
as well. For `gatsby-background-image` installation instructions head over to
its [README](https://github.com/timhagn/gatsby-background-image/tree/main/packages/gatsby-background-image).
For installation instructions of `gatsby-plugin-image`, follow the
aforementioned [migration guide](https://www.gatsbyjs.com/docs/reference/release-notes/image-migration-guide/).

## How to use

```jsx
import { getImage } from "gatsby-plugin-image"

const { placeholderImage } = useStaticQuery(
    graphql`
      query {
        placeholderImage: file(relativePath: { eq: "gatsby-astronaut.png" }) {
          childImageSharp {
            gatsbyImageData(
              width: 200
              placeholder: BLURRED
              formats: [AUTO, WEBP, AVIF]
            )
          }
        }
      }
    `
  );
  const image = getImage(placeholderImage);

  // Use like this:
  const bgImage = convertToBgImage(image);


}
```