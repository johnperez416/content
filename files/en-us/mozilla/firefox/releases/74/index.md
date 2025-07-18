---
title: Firefox 74 for developers
short-title: Firefox 74
slug: Mozilla/Firefox/Releases/74
page-type: firefox-release-notes
sidebar: firefox
---

This article provides information about the changes in Firefox 74 that will affect developers. Firefox 74 was released on March 10, 2020.

## Changes for web developers

### Developer tools

#### Web console

- The `$x()` [web console helper](https://firefox-source-docs.mozilla.org/devtools-user/web_console/helpers/index.html)'s third argument (result type) now accepts simple string values as well as [`XPathResult` constants](/en-US/docs/Web/API/XPathResult#constants) ([bug 1602591](https://bugzil.la/1602591)).
- Freshly landed support for the optional chaining operator "?." which can also be used with Console's autocomplete ([bug 1594009](https://bugzil.la/1594009)).
- The Debugger can now inspect and debug [nested workers](/en-US/docs/Web/API/Web_Workers_API/Using_web_workers) ([bug 1590766](https://bugzil.la/1590766))

### HTML

_No changes._

### CSS

- [`text-underline-position`](/en-US/docs/Web/CSS/text-underline-position) is now enabled by default ([bug 1606997](https://bugzil.la/1606997)).
- The [`text-underline-offset`](/en-US/docs/Web/CSS/text-underline-offset) and [`text-decoration-thickness`](/en-US/docs/Web/CSS/text-decoration-thickness) properties now accept percentage values ([bug 1607534](https://bugzil.la/1607534)).
- The `auto` value of the {{cssxref("outline-style")}} property has been enabled by default ([Firefox bug 1031664](https://bugzil.la/1031664)).

#### Removals

- The `-moz-` prefixed-[Multiple-column layout](/en-US/docs/Learn_web_development/Core/CSS_layout/Multiple-column_Layout) properties have been removed ([Firefox bug 1308636](https://bugzil.la/1308636)).

### SVG

_No changes._

### JavaScript

- The [Optional chaining operator](/en-US/docs/Web/JavaScript/Reference/Operators/Optional_chaining) has been implemented ([Firefox bug 1566143](https://bugzil.la/1566143)).
- When a JavaScript URL (`javascript:`) is evaluated and the result is a string, this string is parsed to create an HTML document, which is then presented. Previously, this document's URL (as reported by the [`document.location`](/en-US/docs/Web/API/Document/location) property, for example) was the originating `javascript:` URL; it is now correctly the URL of the document the `javascript:` URL was evaluated in ([Firefox bug 836567](https://bugzil.la/836567)).

#### Removals

- The `Object.toSource()` method and the global function `uneval()` are no longer available for use by web content or extensions ([bug 1565170](https://bugzil.la/1565170)).

### APIs

#### DOM

- The {{domxref("IDBTransaction.commit()")}} method has been implemented ([Firefox bug 1497007](https://bugzil.la/1497007)).

#### DOM events

- Firefox 74 now supports the {{domxref("WorkerGlobalScope.languagechange_event", "languagechange_event")}} event and its companion event handler property, `onlanguagechange`, which is triggered when the user changes their preferred language ([Firefox bug 1154779](https://bugzil.la/1154779)). This was previously listed in our [compatibility database](https://github.com/mdn/browser-compat-data) as supported from Firefox 3.5, but this was in error.

#### Canvas and WebGL

- The {{domxref("TextMetrics")}} interface has been extended to contain four more properties measuring the actual bounding box — [`actualBoundingBoxLeft`](/en-US/docs/Web/API/TextMetrics/actualBoundingBoxLeft), [`actualBoundingBoxRight`](/en-US/docs/Web/API/TextMetrics/actualBoundingBoxRight), [`actualBoundingBoxAscent`](/en-US/docs/Web/API/TextMetrics/actualBoundingBoxAscent), and [`actualBoundingBoxDescent`](/en-US/docs/Web/API/TextMetrics/actualBoundingBoxDescent). Text metrics can be retrieved using the {{domxref("CanvasRenderingContext2D.measureText()")}} method ([Firefox bug 1102584](https://bugzil.la/1102584)).

#### Removals

- The non-standard `IDBDatabase.mozCreateFileHandle()` method has been removed, in favor of the (also non-standard) `IDBDatabase.createMutableFile()` method ([Firefox bug 1024312](https://bugzil.la/1024312)).
- The non-standard `IDBMutableFile.getFile()` method has been removed ([Firefox bug 1607791](https://bugzil.la/1607791)).
- The non-standard {{domxref("HTMLCanvasElement")}} method `mozGetAsFile()` has been removed, after being deprecated several years ago ([Firefox bug 1588980](https://bugzil.la/1588980)).
- The {{domxref("FetchEvent")}} property {{domxref("FetchEvent.isReload", "isReload")}} has been removed, from both Firefox and the specification ([Firefox bug 1264175](https://bugzil.la/1264175)).

### HTTP

- The [`Cross-Origin-Resource-Policy`](/en-US/docs/Web/HTTP/Reference/Headers/Cross-Origin-Resource-Policy) header is now enabled by default ([bug 1602363](https://bugzil.la/1602363)).

### Security

- TLS 1.0 and 1.1 support has been removed from Firefox; you'll need to make sure your web server supports TLS 1.2 or 1.3 going forward. From now on, Firefox will return a [Secure Connection Failed](https://support.mozilla.org/en-US/kb/secure-connection-failed-firefox-did-not-connect) error when connecting to servers using the older TLS versions ([Firefox bug 1606734](https://bugzil.la/1606734)).
- Starting in Firefox 74, when a site delegates permission to access a resource to embedded content in an {{HTMLElement("iframe")}} using the [`allow`](/en-US/docs/Web/HTML/Reference/Elements/iframe#allow) attribute, and the embedded page requests permission to use that resource, the parent page prompts the user for permission to use the resource and share it with the embedded domain, rather than both the outer and inner pages prompting the user for permission. If the outer page doesn't have the permission requested by the `allow` attribute, the `<iframe>` is immediately denied access without prompting the user [Firefox bug 1483631](https://bugzil.la/1483631).

### Plugins

_No changes._

### WebDriver conformance (Marionette)

- Added `WebDriver:Print` to print the current page as a PDF document ([Firefox bug 1604506](https://bugzil.la/1604506)).
- `Webdriver:TakeScreenshot` now always captures the top-level browsing context and not the currently-selected browsing context, if no element to capture has been specified ([Firefox bug 1398087](https://bugzil.la/1398087), [Firefox bug 1606794](https://bugzil.la/1606794)).
- Using `Webdriver:TakeScreenshot`'s `full` argument causes the complete page to be captured ([Firefox bug 1571424](https://bugzil.la/1571424)).

## Changes for add-on developers

### API changes

- Shortcut keys can now be unassigned in {{WebExtAPIRef("Commands.update")}} by passing an empty value of `shortcut` [Firefox bug 1475043](https://bugzil.la/1475043).
- `urlClassification`s are now returned as part of the `details` in each event of {{WebExtAPIRef("webRequest")}}, providing information on whether a request is classified as fingerprinting or tracking [Firefox bug 1589494](https://bugzil.la/1589494).

### Manifest changes

_No changes._

## See also

- Hacks blog post: [Security means more with Firefox 74](https://hacks.mozilla.org/2020/03/security-means-more-with-firefox-74-2/)
