[npm badge]: https://badge.fury.io/js/sync-glitch-cli.svg
[npm url]:   https://badge.fury.io/js/sync-glitch-cli
[build badge]: https://travis-ci.org/sotayamashita/sync-glitch-cli.svg?branch=master
[build url]:   https://travis-ci.org/sotayamashita/sync-glitch-cli
[codecov badge]: https://codecov.io/gh/sotayamashita/sync-glitch-cli/branch/master/graph/badge.svg
[codecov url]:   https://codecov.io/gh/sotayamashita/sync-glitch-cli
[greenkeeper badge]: https://badges.greenkeeper.io/sotayamashita/sync-glitch-cli.svg
[greenkeeper url]:   https://greenkeeper.io/

# sync-glitch-cli [![npm][npm badge]][npm url] [![build status][build badge]][build url] [![codecov][codecov badge]][codecov url] [![greenkeeper status][greenkeeper badge]][greenkeeper url]

<p>
  <a href="https://www.buymeacoffee.com/pM9aX60">
    <img src="https://www.buymeacoffee.com/assets/img/guidelines/download-assets-sm-1.svg" height="41px" />
  </a>
</p>

> Sync changes in your GitHub repository to glitch.com

**Heads-up!** It uses a API which is not introduced by Glitch officially so it has possibility to be changed without any notice. However, I am making efforts to know wether it works or not with [test-sync-glitch-cli](https://github.com/sotayamashita/test-sync-glitch-cli). It execute test everyday with TravisCI. It help my recognize as soon as possible if it could be wrong. I am looking forward to official API. :unicorn:

## Install

```console
npm install sync-glitch-cli --save-dev
```

## Usage

### How to get required environment variables

1. Open your project on Glitch
1. Open devtool and click the Network tab
1. Select Project name > Advanced Options > Import from GitHub
1. You can find a request URL which starts from `https://api.glitch.com/projects/githubImport ~`:

   ![network](https://user-images.githubusercontent.com/1587053/33523225-a779160e-d844-11e7-9dc2-28e9afed9260.png)

1. It has three params. These params are what you need.

### How to set environment variables

You have to set the following environment variables:

- `GLITCH_PROJECT_ID` _(the Glitch project id.)_
- `GLITCH_TOKEN` _(the Glitch token)_
- `GH_REPO` _(the GitHub repo. e.g `sotayamashita/sync-glitch-cli`)_

```console
GLITCH_PROJECT_ID='' GLITCH_TOKEN='' GH_REPO='' ./node_modules/.bin/sync-glitch
```

Enable debug logs:

```console
GLITCH_PROJECT_ID='' GLITCH_TOKEN='' GH_REPO='' DEBUG=sync-glitch* ./node_modules/.bin/sync-glitch
```

### with Travis CI

```yml
# .travis.yml
after_success:
  - sync-glitch
```

Enable debug logs:

```yml
# .travis.yml
after_success:
  - DEBUG=sync-glitch* sync-glitch
```

- [The Build Lifecycle](https://docs.travis-ci.com/user/customizing-the-build/#The-Build-Lifecycle)
- [Environment Variables](https://docs.travis-ci.com/user/environment-variables/)
