# You should protect your app secrets!

Security is a concern for applications that use secret(s) to integrate with other services. Source Control, the tool used to keep track of code, will reveal these secrets(s) if posted publicly for anyone to view. One of the most popular public Source Control tools is Git->GitHub, which allows developers teams to use its public platform. Although private options are available for GitHub, many projects uses the public version. One could then imagine how insecure an app is when you see a connection string or worse yet, an API key for a popular resource just waiting for someone to grab up. Shouldn't we protect this confidential information?

## So how do you keep your secrets safe?

I have several projects I haven't updated to my public GitHub that I would love to share however, I haven't because they all have secrets I want to protect. Due to the fact that I was in a bit of a time crunch to complete several on-going projects, I did not have enough time to fully complete my research for protecting secrets. I did end up finding few NPM packages that can protect code secrets. The process would allow you to secure your code before check-in and then check-out and decrypt secrets with full developer management by email. Although this would work for what I was looking for, I wanted something lighter, easier to use, and some documentation would help :). I didn't want it to be coupled to git processes and although the developer management feature was awesome, I had no need for it at the time. I then attempted to work on completing a solution for my home projects. Once I had almost completed all the tasks for this solution, it turns out that the same issue came up at work as we were using GitHub Enterprise. Here, developer management would be a nice to have, but my solution seemed like a fit as the new team was not familiar with the stack. Even though it's all internal it didn't seem right for me to save SQL password, connection string and API keys in the repository in raw format. This has to go against best practices. I then released my new package:

> ## [cs-app-secrets](https://www.npmjs.com/package/cs-app-secrets) for npm 

- Encryption of file contents.
- Encryption of provided secret text.
- All referenced in package.json or provided config file.
- Full CLI (Command Line) options & help provided.
- NodeJs in app usage for build script or runtime decryption.
- 1 Master Key.
- Environment variable usage.

Here's the flow: Once installed and initialize with your configuration file (package.json default), you can add new secrets:

**WITHOUT** Environmental **MASTER-KEY** set in terminal and **NOT** installed Globally:

`node node_modules/cs-app-secrets --add [MY-NEW-SECRET-KEY] [MY-NEW-SECRET-VALUE]  --secret [MASTER-KEY-FROM-INITIALIZATION]`

VS everything set:

`cs-app-secrets --add [MY-NEW-SECRET-KEY] [MY-NEW-SECRET-VALUE]`

or add a file:

`cs-app-secrets --add [MY-NEW-SECRET-KEY] [MY-NEW-SECRET-FILE-PATH]`

get the value:

`cs-app-secrets --get [MY-NEW-SECRET-KEY]`

after all secrets are added and you just want to read the values from the configuration file; decrypt all:

`cs-app-secrets --revealAll`

need help:

`cs-app-secrets --help`

use on the fly at runtime in code. 

`csAppSecrets.get('[MY-NEW-SECRET-KEY]');` See [FULL EXAMPLE HERE](https://www.npmjs.com/package/cs-app-secrets)

Now I can protect API Keys, password and other secrets using my MASTER-KEY which I can add to my build configuration processes such as Jenkins, use local /server environmental variables, pre decrypt in JSON or at runtime in JavaScript or TypeScript. 

If you want something fast, light, easy to use, and still provides protection of the secrets in your code stored publicly on GitHub or GitHub Enterprise check out: https://www.npmjs.com/package/cs-app-secrets