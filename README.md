# gatsby-source-local-git

[![npm](https://img.shields.io/npm/v/gatsby-source-local-git?style=flat-square&logo=npm)](https://www.npmjs.com/package/gatsby-source-local-git)
[![MIT](https://img.shields.io/github/license/pmudra/gatsby-source-local-git?style=flat-square)](https://github.com/PMudra/gatsby-source-local-git/blob/master/LICENSE)
[![build](https://img.shields.io/github/workflow/status/PMudra/gatsby-source-local-git/Node%20CI?logo=github&style=flat-square)](https://github.com/PMudra/gatsby-source-local-git/actions)

A Gatsby source plugin for sourcing data into your Gatsby application from your local git repository.

<!-- ## Description

Include a summary of what this plugin accomplishes. Is there a demo site that shows how this plugin operates? If so, include a link to the deployed demo site and/or its source code here. -->

## How to install

`npm install --save gatsby-source-local-git`

<!-- ## Available options (if any) -->

<!-- ## When do I use this plugin?

Include stories about when this plugatsby-source-local-gitgin is helpful and/or necessary. -->

## Examples of usage

```javascript
// In your gatsby-config.js
module.exports = {
  plugins: [`gatsby-source-local-git`],
}
```

## How to query for data

### Commits

You can query commit nodes like the following:

```graphql
{
  allGitCommit(limit: 25, sort: { fields: date, order: DESC }) {
    edges {
      node {
        hash
        message
        body
        date(fromNow: true)
        refs
        author {
          name
          email
        }
      }
    }
    totalCount
  }
}
```

Query hash of latest commit:

```graphql
{
  gitCommit(latest: { eq: true }) {
    hash
  }
}
```

### Tags

You can query tags like this:

```graphql
{
  allGitTag {
    edges {
      node {
        name
      }
    }
  }
}
```

Query the latest tag:

```graphql
{
  gitTag(latest: { eq: true }) {
    name
  }
}
```

Tags will simply be sorted by semantic version number to find the latest tag (including every tag containing a dot like `v1.2.3` or `1.2` but not `newest-feature`).

### Branches

You can query branches like this:

```graphql
{
  allGitBranch {
    edges {
      node {
        commit
        id
        name
        current
      }
    }
  }
}
```

Query the current branch:

```graphql
{
  gitBranch(current: { eq: true }) {
    name
  }
}
```

### Authors

You can query author nodes like the following:

```graphql
{
  allGitAuthor(sort: { fields: name }) {
    nodes {
      name
      email
    }
    totalCount
  }
}
```

<!-- ## How to run tests

## How to develop locally

## How to contribute

If you have unanswered questions, would like help with enhancing or debugging the plugin, it is nice to include instructions for people who want to contribute to your plugin. -->
