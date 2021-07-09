## Directory Structure

When developing, you will be living inside the `src` directory. This directory has the following structure be default:

```sh
src
├── components
│   ├── Layout.js
│   ├── Modal.js
│   ├── ModalContext.js
│   └── SEO.js
├── images
│   └── icon.png
├── pages
│   ├── 404.js
│   └── index.js
├── partials
└── templates
    ├── blog.js
    ├── page.js
    └── post.js
```

**components**

This directory contains _single file_ React components. Inside a component file, there will be a default export that defines that component. Inside this component file will be all the styles and functionality for this component.

**images**

This directory contains images that can be included from components and partials. Image optimization happens at build time, so there is no need for these images to be optimized or be in a certain format.

**pages**

This behaves as Gatsby's default pages directory. By default, Gatsby will use index.js and 404.js to represent the home page and 404 error pages respectively. If the page's title matches the name of a file in this folder, Gatsby will automatically apply the page file to build that page. For more info, see Gatsby's [docs](https://www.gatsbyjs.com/docs/creating-and-modifying-pages/).

**partials**

For larger React components, it becomes necessary to separate the styles from the components. In this directory, _folder components_ are defined for larger React components, usually representing sections of the website. An example partial named FrontHero would look like this:

```sh
partials
├── FrontHero
    ├── index.js
    ├── styles.js
```

`index.js` contains a default export that will be used when the partial is imported. `styles.js` defines all the styles that the component will use, to make it look cleaner. This will make more sense when you are actually developing partials, and can see why folder components become necessary.

**templates**

If a page has a template set in WordPress, EDS will automatically try to match its name against a file in this list. For example, if the template's name is `A Very Cool Template`, EDS will search for `a-very-cool-template.js` in this directory. If it exists, the page will be created with this file instead of falling back to the default `page.js`.

## Components

Components are single-file React components that represent a single feature on a webpage. They are typically small and reusable in different locations on a site. For example, a form is probably what we call a component, but a footer _containing_ the form would be a partial.

You can create a new component easily by running this Esquire CLI command **from the root directory**:

```sh
esquire component ComponentName
```

Be sure that your component names are always **capitalized** and not snake-case (componentName). This is just a React standard that will make your directories and code more readable. The newly created file will have the boilerplate code needed to get started developing the component:

```js
import React from "react";
import tw, { styled } from "twin.macro";

const ComponentNameStyles = tw.p`block`;

const ComponentName = ({ prop, ...rest }) => (
  <ComponentNameStyles {...rest}>Edit me</ComponentNameStyles>
);

export default ComponentName;
```

Make sure to always have a default export that is the React component you want this file to represent. The actual name of the variable you export does not matter. Now, from any file (component, partial, page, etc.) you can import your new component:

```js
import ComponentName from "@/ComponentName";
```

Webpack will match `@` to the components folder, no matter what directory or subdirectory you are in. It is wise to leave GraphQL queries out of components and instead send any data needed as a prop. This way, components are not static and can be reused and take on many forms.

## Partials

For larger sections of a web page you are often querying information from GraphQL to display. For example, a `FrontHero` partial likely has several fields in an option page that contains the information to display, and a front hero will only ever display this information. In this sense, the partial is **static**. It will always take the information from the front hero fields.

Because it is a large section of the site and queries its own data, it is distinguished as a partial. Partials are _folder_ react components, meaning they contain two files. `index.js` is what will be included when you include the partial, and contains the default export just like a component. However, it imports the styles (because there can be many) from `styles.js` that lives in the same file.

It's easier to understand once you have code in front of you. You can generate a partial using the Esquire CLI in the root directory:

```sh
esquire partial FrontHero
```

This will create a new directory, `src/partials/FrontHero`, with two files in it. Firstly, `index.js` will look like this:

```js
import React from "react";
import { graphql, StaticQuery } from "gatsby";
import { Section } from "./styles";

const FrontHero = () => (
  <StaticQuery
    query={graphql`
      query {
      }
    `}
    render={(data) => {
      // const fields = data.wp
      return <Section className="fronthero"></Section>;
    }}
  />
);

export default FrontHero;
```

This uses the `StaticQuery` component from Gatsby. To learn more about static queries, read their [docs](https://www.gatsbyjs.com/docs/how-to/querying-data/static-query/). Essentially, the result of the GraphQL query inside the query prop will be passed as `data` into the render prop. This can then be accessed in functional component inside the render prop, which is where all your styled components will be laid out.

Inside `styles.js`, you will export all the styled components you will use in the render of the `StaticQuery` in `index.js`. For example, if I wanted to add a styled title to the hero component, I would add the styling to `styles.js`:

```js
import tw, { styled, css } from "twin.macro";

export const Section = styled.section`
  ${tw`w-full flex items-center justify-center flex-col text-center`}
`;

// Define a styled title to import
export const Title = tw.h1`text-3xl font-bold font-mont leading-tight`;
```

And import it and use it in `index.js`:

```js
import React from "react";
import { graphql, StaticQuery } from "gatsby";
import { Section, Title } from "./styles"; // Added the import for the title

const FrontHero = () => (
  <StaticQuery
    query={graphql`
      query {
        wp {
          frontHero {
            frontHero {
              title
            }
          }
        }
      }
    `}
    render={(data) => {
      const fields = data.wp;
      return (
        <Section className="fronthero">
          <Title>{fields.frontHero.frontHero.title}</Title> // Added title
        </Section>
      );
    }}
  />
);

export default FrontHero;
```

Partials can be imported similarly from any file using the `Partials` path:

```js
import FrontHero from "Partials/FrontHero";
```

Notice there is no index.js or relative path. Webpack will find the `index.js` in the `FrontHero` folder, and include it no matter where the import is located.
