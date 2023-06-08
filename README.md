# Instructions for admins

To add the [Bird UI theme](https://github.com/ronilaukkarinen/mastodon-bird-ui) to your Mastodon instance follow these steps... meow..!



1. Add the files from the repo (elephant-*.scss) and the folder elephant to your Mastodon themes directory:

```
app/
  javascript/
    styles/
    elephant.scss                             | **new**
    elephant-contrast.scss                    | **new**
    elephant-light.scss                       | **new**
      contrast/
        ...
      fonts/
        ...
      elephant/                               | **new**
        layout-multiple-columns.scss          | **new**
        layout-single-column.scss             | **new**
```


2. **Add your themes to the config.** This is what [the default themes.yml](https://github.com/tootsuite/mastodon/blob/master/config/themes.yml) looks like in Mastodon. To make your custom themes visible in settings, you need to add a new line in the form `themeName: path/to/theme.scss`. For example, the modern-dark theme would require adding `modern-dark: styles/modern-dark.scss` as a new line.

```
        default: styles/application.scss
        contrast: styles/contrast.scss
        mastodon-light: styles/mastodon-light.scss
        elephant: styles/elephant.scss                    | **new**
        elephant-contrast: styles/elephant-contrast.scss  | **new**
        elephant-light: styles/elephant-light.scss        | **new**
```

3. **Add a human-friendly name for the themes (optional).** You can edit each desired language's locale file in `config/locales/[lang].yml` to add a localized string name for your theme's `themeName` as added in the previous step. For example, [the default `config/locales/en.yml`](https://github.com/tootsuite/mastodon/blob/041ff5fa9a45f7b8d1048a05a35611622b6f5fdb/config/locales/en.yml#L942-L945) contains localizations for the three default themes that ship with Mastodon, into the `en`glish language. You need to do this for every language you expect your users to use, or else they will see the unlocalized `themeName` directly.

```
          themes:
            contrast: Mastodon (High contrast)
            default: Mastodon (Dark)
            mastodon-light: Mastodon (Light)
            elephant: Elephant                            | **new**
            elephant-contrast: Elephant (High contrast)   | **new**
            elephant-light: Elephant (Light)              | **new**
```

4. **Compile theme assets and restart.** Run `RAILS_ENV=production bundle exec rails assets:precompile` and restart your Mastodon instance for the changes to take effect.
