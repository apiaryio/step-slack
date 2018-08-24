# step-slack

A slack notifier written in `bash` and `curl`. Make sure you create a Slack
webhook first (see the Slack integrations page to set one up).

[![wercker status](https://app.wercker.com/status/94f767fe85199d1f7f2dd064f36802bb/s "wercker status")](https://app.wercker.com/project/bykey/94f767fe85199d1f7f2dd064f36802bb)

# Options

- `url` The Slack webhook url
- `username` Username of the notification message
- `channel` (optional) The Slack channel (excluding `#`)
- `icon_url` (optional) A url that specifies an image to use as the avatar icon in Slack
- `notify_on` (optional) If set to `failed`, it will only notify on failed
builds or deploys.
- `branch` (optional) If set, it will only notify on the given branch


# Example

```yaml
build:
    after-steps:
        - slack-notifier:
            url: $SLACK_URL
            channel: notifications
            username: myamazingbotname
            branch: master
```

The `url` parameter is the [slack webhook](https://api.slack.com/incoming-webhooks) that wercker should post to.
You can create an *incoming webhook* on your slack integration page.
This url is then exposed as an environment variable (in this case
`$SLACK_URL`) that you create through the wercker web interface as *deploy pipeline variable*.

# License

The MIT License (MIT)

# Changelog

## 1.6.5

- Using WERCKER_GIT_COMMIT as build ID
- Fix typo

## 1.6.4

- Better hash formating (added # char)

## 1.6.3

- Using `WERCKER_RUN_ID` instead `WERCKER_BUILD_ID` that is only in build workflow
- Added default Sucess for `WERCKER_RESULT` if notifier isn't run in after steps.
- Rename `RESULT` to `MESSAGE_RESULT` to prevent conflict in script

## 1.6.2

- Fixed missing link in message

## 1.6.1

- Better message format

## 1.6.0

- `$WERCKER_BUILD_URL` replaced by `$WERCKER_RUN_URL`
- git branch is link in message

## 1.2.0

- Added `branch` option

## 1.1.0

- `channel` is now optional (wercker/step-slack#5)

## 1.0.0

- Initial release

## Contributing to this repository

Oracle welcomes contributions to this repository from anyone.  Please see [CONTRIBUTING](CONTRIBUTING.md) for more information.
