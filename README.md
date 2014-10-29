Alternative TYPO3 composer installers
=====================================

This is a derivative of the official TYPO3 composer installers at
https://github.com/TYPO3/CmsComposerInstallers

I prefer to differentiate strictly between 'automatically installed sources'
(by composer, that go into the vendor directory and can be automatically
overwritten again) and 'manually mangled sources'
(by me, editable, outside of the vendor directory).

My alternative installer mode installs TYPO3 core and extensions in the 
vendor directory, symlinking the latter into `typo3/ext`. As it is absolutely
necessary, a single symlink `typo3_src` is written in the web root directory.

== Configuration Options

Extra option       | Description
------------------ | -----------
`typo3_vendor_based` | (boolean) whether to use my alternative mode
`typo3_web_dir`      | (string) web root directory, defaults to composer project directory.

A composer.json might look like:

```json
{
        "repositories": [
                {
                        "type": "composer",
                        "url": "http://composer.typo3.org/"
                },
                {
                        "type": "vcs",
                        "url":  "http://github.com/KampfCaspar/CmsComposerInstallers.git"
                }
        ],

        "require": {
                "typo3/cms-composer-installers": "1.1.x-dev",
                "typo3/cms": "~6.2",
                "typo3-ter/news": "*",
                "typo3-ter/html5videoplayer": "*",
                "typo3-ter/cooluri": "*",
                "typo3-ter/ke-search": "*",
                "typo3-ter/powermail": "*",
                "typo3-ter/sr-freecap": "*"

        },

        "extra": {
                "typo3_web_dir": "html",
                "typo3_vendor_based": true
        }

}
```

The explicit mentioning of `cms-composer-installers` should protect against
hidden errors if the original gets updated beyond the point of this
derivative.
