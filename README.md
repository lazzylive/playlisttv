<div align="center">
    <b>English</b> | <a href="README-it.md">Italiano</a>
</div>

# Info on local development
## Prepare the development environment
1. Clone the repo: `git clone https://github.com/ZapprTV/Zappr`
2. Install the dependencies: `npm install` (or `pnpm install`)
3. Edit the `public/config.json` file if necessary

The `public/config.json` file is the file that contains, other than the API's URLs, the URLs to the channel lists and logos. By default it uses the ones hosted by Zappr (`channels.zappr.stream`), but if you need to use a local copy, clone the relevant repo:

`git clone https://github.com/ZapprTV/channels`

Then edit `public/config.json` to make it point to your local copy:
```json
    "channels": {
        "host": "/channels"
    },
    [...]
    "logos": {
        "host": "/channels/logos",
        [...]
    },
```

## Next steps
To start up a local server, run `npm run dev` (or `pnpm run dev`).

To initiate a build, which will then end up in the `dist/` folder, run `npm run build` (or `pnpm run build`).
- The build will have the same configuration as the one in `config.json`, and will only include the frontend's files by default. If you also want to include the channel lists' and logos' files, add the command line argument `--bundleChannels`.
    - By default, `--bundleChannels` will download the channel lists and logos from `https://github.com/ZapprTV/channels`, but if you want it to download them from another Git repo or to copy them from a local folder, specify the name of the folder / the Git repo URL **(with .git at the end of it)** in the `--channelsURL` argument.
        - For example, `--channelsURL=Channels` will copy the local folder `Channels` and include it in the build, while `--channelsURL=https://github.com/User123/Channels.git` will clone the GitHub repo `User123/Channels` and include that in the build.
    - **IMPORTANT**: To specify command line arguments with NPM, you have to prefix them with `--`.
        - So, for example, instead of running `npm run build --bundleChannels`, you'll have to run `npm run build -- --bundleChannels`.
        - **This isn't the case with PNPM.** If you're using PNPM you can just run `pnpm run build --bundleChannels`.
