# Developing Plugins for PhoneGap Build

Last updated October 24, 2012.

We are interested in working with partners to develop plugins for use on
PhoneGap Build. Any plugins added to our system right now will be accessible
to all PhoneGap Build users; there may be other mechanisms for PhoneGap Build
plugin usage in the future.

PhoneGap Build supports plugins for iOS and Android. Our focus right now is on
creating a great plugin experience for those two platforms.

There are two considerations when developing a plugin for PhoneGap Build:

1. Developing the plugin code
2. Packaging the plugin for use with our tools

The linked versions of any tools and/or specifications are the ones used by
PhoneGap Build.

## Developing the plugin code

A PhoneGap Plugin consists of:

* a JavaScript file, implementing the PhoneGap Plugin interface. Unless you
have an exceptionally good excuse, the same JavaScript code should run on both
supported platforms
* a native class for each supported platform, implementing the PhoneGap Plugin
interface
* associated dependencies and assets. There may, for instance, need to be
multiple native classes to implement the full plugin logic, or UI assets on the
native or www side.

Plugins developed for PhoneGap Build should always be developed and tested
against the latest release of PhoneGap (2.1 at the time of writing).

Up to date information about plugin development is available at 
[docs.phonegap.com][pgdocs]

## Packaging the plugin

PhoneGap Build uses the [pluginstall][pins] tool to install plugins into the
native projects we generate for our users. We are currently using the `0.5.0`
release of pluginstall.

The correct format for plugins used by pluginstall is documented in
[a separate spec][spec]. For an example of a plugin built according to that
spec, please see [the ChildBrowser plugin][child], which is currently active
on PhoneGap Build.

To check whether your plugin is packaged correctly for each supported platform:

1. Create a new Cordova project for that platform. Edit the generated
`index.html` file to reference and use your plugin
2. Run the correct pluginstall command. For instance, if you're installing a
plugin stored in `/Users/alunny/dev/plugin` into an iOS project stored in
`/Users/alunny/dev/my_project`, run:

    `pluginstall ios /Users/alunny/dev/my_project /Users/alunny/dev/plugin`

3. Verify that the project can build without error, that the plugin is
included, and that any JavaScript code using the plugin executes correctly.

All of the above tools and specifications are in active development. If you find
a limitation or an error with pluginstall or the specification, please create
an issue on the appropriate GitHub project.

## Submitting Your Plugin

Once your plugin is in a state that you're happy with, please email
build@phonegap.com and we'll take the next steps to get the plugin integrated
on PhoneGap Build.

Our criteria for including the plugin on PhoneGap Build, broadly speaking, are:

1. We believe it legitimately adds value for our users.
2. We can build an app using your plugin, and verify that it works.
3. We can do a quick review of the source code, and flag anything that concerns
us (security risks, compiler warnings, that sort of thing).

If we're not satisfied with any of the above, we'll get back to you with our
concerns, and hopefully we can reach a resolution. If you're worried that your
plugin will not meet our standards, please get in contact while you're
developing so we can help you out.

We are still figuring out our deployment strategy for plugins, so the timeframe
for getting a plugin onto the system is currently unknown. Once we have a
process established with multiple plugins, this document will be updated.

## Authors

@alunny

[pgdocs]:http://docs.phonegap.com/en/2.1.0/guide_plugin-development_index.md.html
[pins]:https://github.com/alunny/pluginstall
[spec]:https://github.com/alunny/cordova-plugin-spec
[child]:https://github.com/alunny/ChildBrowser
