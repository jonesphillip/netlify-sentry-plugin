# Netlify Sentry plugin &nbsp;&nbsp;&nbsp;<a href="https://app.netlify.com/start/deploy?repository=https://github.com/jonesphillip/netlify-sentry-plugin"><img src="https://www.netlify.com/img/deploy/button.svg"></a>

Automatically notify [Sentry](https://sentry.io/) of new releases being deployed to your site after it finishes building in Netlify.

The Netlify Sentry build plugin:
* Notifies Sentry of new releases being deployed
* Uploads source maps to Sentry
* Sends Sentry the commit SHA of HEAD to enable commit features

Before proceeding, you'll first want to ensure that your Sentry project is set up properly to track commit metadata. The easiest way to do that is to [install a repository integration](https://docs.sentry.io/workflow/releases/?platform=python#install-repo-integration).

Make sure build plugins are enabled on your site to see the plugin run.

## Installation

To install, add the following lines to your `netlify.toml` file:

```toml
[[plugins]]
  package = "netlify-plugin-sentry"
```

Note: The `[[plugins]]` line is required for each plugin, even if you have other plugins in your `netlify.toml` file already.

## Configuration

Configure the plugin with your sentry settings.

```toml
[[plugins]]
  package = "netlify-plugin-sentry"

  [plugins.inputs]
    sentryOrg = ""
    sentryProject = ""
    sentryEnvironment = ""
    sentryAuthToken = ""
    sourceMapPath = ""
    sourceMapUrlPrefix = ""
```

For more information about the parameters above, please see the [Sentry release management docs](https://docs.sentry.io/cli/releases/).

You can also use [site environment variables](https://docs.netlify.com/configure-builds/environment-variables/) to configure these values.

- `process.env.SENTRY_ORG` - The slug of the organization name in Sentry
- `process.env.SENTRY_PROJECT` - The slug of the project name in Sentry
- `process.env.SENTRY_ENVIRONMENT` - The name of the environment being deployed to
- `process.env.SENTRY_AUTH_TOKEN` - Authentication token for Sentry
