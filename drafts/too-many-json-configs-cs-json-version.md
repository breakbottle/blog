# Too many JSON configs

Every application will have a configuration file that also defines the app's version. This is extremely convenient when you are trying to determine which version of this app or package to use. For most NodeJS apps, this is the `package.json` config file, if the app owner chooses to use this file as the source of truth. 

A couple of years ago I was working on a personal full-stack solution that included many configuration files for both Front-end and back-end. These files included the `package.json`, `bower.json`, a php plugin for `wordPress` JSON and since JSON configs were very common at the time, I had my own JSON to define configs for `PHP` + custom app options. Concurrently, at work I had a similar issue where the main project had a library of tools. Each tool had it's own version however, they were all released together and all needed a to reflect the same deployment version in configs, due to dependencies & support. 

Facing these issues, I wanted a way to run one process the will update all JSON files with the same version, updating the version property. My search at the time only showed solutions that were specific to package managers or tools. As a result, I created: 

> ### [cs-json-version](https://www.npmjs.com/package/cs-json-version) for npm. 

Then I started to get a bit carried away thinking up use-cases and adding features :smile: :

- VSCode text-editor command-bar customization.
    > Adding a icon-text button in the status bar
- Gulp taskRunner.
    > Add a Gulp tasks to update the version.
- CLI: CommandLine / script.
    > Add a snippet of code in a file that is executed via node.
- Pre-Commit Hooks for git.
    > As you commit it will update the version first before adding you changes.
- Auto git commit and tag.
- Auto create `semantic version` if no version is provided based on staged files.
- Auto push to desired `git branch`.

I then had enough options for integration, builds and one time use. Today I still use on my personal projects even though they are smaller and recommend at work when I see a use case. It is useful having not to worry about how much work was done or tasks completed to think up minor version, as major and patch is easier defined. The auto increment and auto commit + tag features provides one less thing to worry about knowing all my version in the app are updated correctly.

Hope this is useful for others check it out: https://www.npmjs.com/package/cs-json-version
