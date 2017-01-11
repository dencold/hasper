# Change Log
All notable changes to this project will be documented in this file.

- The format is based on [Keep a Changelog](http://keepachangelog.com/) 
- This project adheres to [Semantic Versioning](http://semver.org/)

## [Unreleased]
- Headers are no longer **bold**, affects page titles, etc. [#22](https://github.com/dencold/hasper/issues/22)
- Making max-width 800px, up from 720px. I prefer a little longer line length on posts. [f44c174](https://github.com/dencold/hasper/commit/f44c17489c5965c2d433126bfebb4df00ee9950f)
- Author metadata now provides helpful links to the corresponding author detail page [#23](https://github.com/dencold/hasper/issues/23)
- Display of copyright only references `.Site.copyright` field (previously we also had `.Site.Params.hideCopyright`).
- Hasper now supports [Creative Commons](https://creativecommons.org/choose/) licenses via the `.Site.Params.creativeCommons` parameter. Set it and you'll have an icon in the footer representing you license type. [#8](https://github.com/dencold/hasper/issues/8)

## 0.0.2 - 2016-08-24
### Changed
- Replaced author.name with author.firstName and author.lastName, make sure to update config.yaml
- Author short names are referenced from the author.id field, add this to config.yaml as well

### Added
- Author metadata follows upcoming Hugo change [#13](https://github.com/dencold/hasper/issues/13)
- Cover image size is now configurable via `fullCover` property [#12](https://github.com/dencold/hasper/issues/12)

## 0.0.1 - 2016-08-08
### Added
- Initial CHANGELOG file to keep track of changes to Hasper over time.
- Additionally, Hasper now uses semver and properly tags releases.

## Attribution

Hasper was originally a fork of the [hugo-theme-casper](https://github.com/vjeantet/hugo-theme-casper). However, the original author was not responding to [pull requests](https://github.com/vjeantet/hugo-theme-casper/pull/41). Hasper now lives as its own separate repository and has been updated with the following improvements: 

- author thumbnail fixes across the site (original version only worked on list template): [25467fc](https://github.com/dencold/hasper/commit/25467fc92ca611ae7a6d517c16b47cdac0ae9dcb)
- switching from bespoke `.Site.Data.Author` in favor of Hugo's canonical `.Site.Author`: [25467fc](https://github.com/dencold/hasper/commit/25467fc92ca611ae7a6d517c16b47cdac0ae9dcb)
- icon aesthetic improvements, previous styles had ugly underlines: [2238091](https://github.com/dencold/hasper/commit/22380914098cbf0dad119be18d7727521f097a29)
- removing unused `page` directory which contained duplicate code: [8c2f9e8](https://github.com/dencold/hasper/commit/8c2f9e8c5b138d89e1b5e2c39d2d6210c928ad9f)
- allowing for external image linking (gravatar, twitter, etc), original theme hardcoded site's base url: [06afad2](https://github.com/dencold/hasper/commit/06afad23845e6e51c0ac55cef29c2e7caf7878d5)
- share icons are now user-configurable: [b334fed](https://github.com/dencold/hasper/commit/b334fed9c5e88447b98e5908c362f3d165e1ee02)
- full theme support for [highlightjs](https://highlightjs.org/) code blocks: [a8f2870](https://github.com/dencold/hasper/commit/a8f2870b03a5d48075129372ad7f499f0ac4c2d4)
