# xkcd-Adopted

### A free, ad-free, open-source, native xkcd.com reader for iOS.

Inspired by [xkcd #306: "Orphaned Projects"](https://xkcd.com/306/) — because every abandoned open-source project deserves a second chance. 🏠

This is a fork of mamaral/xkcd-Open-Source, originally built by Mike Amaral. The original app was on the App Store for years and was a great way to read xkcd. The repo hasn't seen activity since 2020 and the app was eventually removed from the App Store, so this fork exists to keep it available.

<!-- TODO: Replace with App Store badge + link once live -->
<!-- [![Download on the App Store](https://img.shields.io/badge/App_Store-Download-blue?logo=apple)](https://apps.apple.com/app/xkcd-adopted/id__PLACEHOLDER__) -->

![demo](Screenshots/demo.png)


## What changed in the fork

- ✂️ Removed Facebook SDK, Twitter SDK, Fabric, and Crashlytics (all deprecated or sunset by their parent companies)
- 🔒 Replaced social SDK share buttons with the native iOS share sheet (`UIActivityViewController`)
- 📋 Added `PrivacyInfo.xcprivacy` for App Store compliance
- 📱 Bumped deployment target to iOS 18
- 🪦 Removed the Today Extension widget (deprecated by Apple in iOS 14, replaced by WidgetKit)
- 🧹 Vendored CocoaPods dependencies for long-term build reproducibility ahead of the [CocoaPods trunk sunset](https://blog.cocoapods.org/CocoaPods-Specs-Repo/) in December 2026

The app logic, UI, and reading experience are intentionally unchanged from the original. This fork exists to keep the app alive, not to rewrite it.


## Architecture

- [AFNetworking](https://github.com/AFNetworking/AFNetworking) — HTTP networking (classic Obj-C era, predates `URLSession`)
- [Realm](https://github.com/realm/realm-cocoa) — local data store for comic metadata
- [Façade](https://github.com/mamaral/Facade) — UI frame-based layout helper (also by Mike Amaral)
- [SDWebImage](https://github.com/rs/SDWebImage) — async image downloading and caching
- [FLAnimatedImage](https://github.com/Flipboard/FLAnimatedImage) — for that one GIF
- [xkcd-font](https://github.com/ipython/xkcd-font) — because obviously
- Stripped, modified, and customized [Mosaic Layout](https://github.com/betzerra/MosaicLayout) for the comic list


## Privacy

xkcd-Adopted collects no data. No analytics, no tracking, no accounts, no ads. Comics are fetched directly from xkcd.com. That's it. See [PRIVACY.md](PRIVACY.md) for the full privacy policy.


## Building

Pods are vendored in the repo, so building should work without running `pod install`:

```
git clone https://github.com/ranvel/xkcd-Adopted.git
cd xkcd-Adopted
open "xkcd Open Source.xcworkspace"
```

Open the **workspace** (not the `.xcodeproj`), select your target device, and build.

If you need to re-run pod install for any reason:

```
sudo port install ruby34
sudo port select --set ruby ruby34
gem install bundler --user-install
bundle config set --local path 'vendor/bundle'
bundle install
bundle exec pod install
```


## Original Contributors

- [Mike Amaral](https://github.com/mamaral) — architect of the original iOS app
- [Sean Ferguson](https://github.com/fergusean) — architect of the server that pulls content from xkcd and pushes to clients
- [Ryan Copley](https://github.com/RyanCopley) — CI build improvements

## Fork Maintainer

- [ranvel](https://github.com/ranvel) — Cedar Syntax LLC


## Status

This fork is in maintenance mode. If a future iOS update breaks something, I'll try to fix it. Otherwise the app is staying as-is. No new features planned, no pull requests being accepted. If you find a bug, feel free to open an issue for visibility, but no promises on turnaround.

## License

The source is made available under the MIT license. See [LICENSE.txt](LICENSE.txt) for details.

xkcd comics are licensed under [Creative Commons Attribution-NonCommercial 2.5](http://xkcd.com/license.html) by Randall Munroe. The [xkcd-font](https://github.com/ipython/xkcd-font) is licensed under [Creative Commons Attribution-NonCommercial 3.0](https://github.com/ipython/xkcd-font/blob/master/LICENSE).

Social sharing icons from [Zlatko Najdenovski](https://www.iconfinder.com/zlaten) via a [Creative Commons Attribution 3.0 Unported License](http://creativecommons.org/licenses/by/3.0/).


## Disclaimer

xkcd-Adopted is a community fork of an open-source project. It is not affiliated with, endorsed by, or connected to [xkcd.com](https://xkcd.com), Randall Munroe, or the original developer Mike Amaral. All xkcd content is the property of Randall Munroe and is used in accordance with the [xkcd license](http://xkcd.com/license.html).