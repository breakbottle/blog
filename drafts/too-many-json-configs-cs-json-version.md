# Too many JSON configs

![cs-json-version an npm package](https://breakbottle.github.io/blog/img/too-many-json-configs-cs-json-version.png "cs-json-version an npm package")

Every application will have a configuration file that defines the app's version. This is extremely convenient when you are trying to determine which version of this app or package to use. For most NodeJS apps, this is the `package.json` config file. If the app owner chooses to use this file as the source of truth. But what happens when an application has multiple JSON configuration files that specify the version of the application?

### How do you keep them all in sync?

A couple of years ago, I was working on a personal full-stack solution that included many configuration files for both Front-end and back-end technologies. These files included the `package.json`, `bower.json`, a PHP plugin for `wordPress` JSON, and since JSON configs were very common at the time, I had my own JSON to define configs for `PHP` + custom app options. Concurrently, at work I had a similar issue where the main project had a library of tools. Each tool had it's own version, however, they were all released together. They all needed to reflect the same deployment version in configs due to dependencies & support. 

Facing these issues, I wanted a way to run one process that will update all JSON files with the same version to update the `version` property. My search at the time only showed solutions that were specific to package managers or tools. As a result, I created: 

> ### [cs-json-version](https://www.npmjs.com/package/cs-json-version) for npm. 

Then, I started to get a bit carried away, coming up with use-cases and adding additional features :smile: :

- VSCode text-editor command-bar customization.
    > Adding a icon-text button in the status bar.
- Gulp taskRunner.
    > Add a Gulp tasks to update the version.
- CLI: CommandLine / script.
    > Add a snippet of code in a file that is executed via node.
- Pre-Commit Hooks for git.
    > As you commit it will update the version first before adding your changes.
- Auto git commit and tag.
- Auto create `semantic version` if no version is provided based on staged files.
- Auto push to desired `git branch`.

I now had enough options for integrations, builds, and one time use. Today I still use this package on my personal projects and recommend at work when see fit. It is useful to not have to worry about how much work was done or how many tasks were completed, as the minor semantic version number is usually more challenging vs the major or patch version number is easier to define. The auto increment and auto commit + tag features provides one less thing to worry about, knowing all my versions in the app are updated correctly.

Hope this is useful for others check it out: https://www.npmjs.com/package/cs-json-version
