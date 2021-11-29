# AuthGateway Portal

[Hugo] theme to quickly create application catalogues.
In this context, an application catalogue is a simple web page to collect references to other
web applications.

This provides a single known location useful to then reach out to many other links/tools.
While all items in a catalogue generally have a common thread, that does not have to be the case.

The AuthGateway Portal theme are great for creating a "one link to rule them all" page for
homes and small busnesses.
When combined with [AuthGateway] you can have a secured collection of locally or remotely
accessible tools at your fingertips.

Intended to be used in combination with the [AuthGateway] authentication proxy.
This theme can also be used independendly.

## Boostrap Framework

This theme uses the [Bootstrap framework].

The [Bootstrap framework] is provided as part of the static assets
in this theme directly instead of using external CDNs.
This allows the theme to remain independent of external services.

The Bootsrap assets included in this theme are the official minified versions fetched
for the [Bootstrap framework] distribution bundle.

## Usage

While this is technically a [Hugo] theme and can be used as such the intention is to
quickly create protals from a list of catalogue entries.

Entries are specified in a [Hugo data file](https://gohugo.io/templates/data-templates/).
By default data is looked up in the `catalogue` "collection".
The Hugo site parameter `catalogue` can be set to a different data "collections" to use.

Catalogue file schema, in YAML format:

```yaml
---
# Catalogue files must be list of entry objects.
- title: Title of card for the entry
  # The description field is optional. If present it will be added to the card.
  # Useful to provide a quick overview of what the entry points to.
  description: Optional description for the enty.
  # An indicator of the "protection level" for the entry.
  # Possible values are:
  # - audited
  # - link
  # - partial
  # - protected
  # If a tag is not set the entry is tagged as `unknown`.
  tag: link
  # The URL to access the catalogue entry with.
  url: https://service.yourdomain.local/
```

```toml
# The site title is displaied in the top bar by default.
title = "AuthGateway Portal Example"
# Base URL where your catalogue is served from.
baseURL = "https://portal.yourdomain.local"
# Activate the catalogue system 
theme = "auth-gateway-portal-hugotheme"

# Disable all default features that don't really make sense for our use case.
disableKinds = ["section", "taxonomy", "term", "RSS", "sitemap"]
# The robots.txt from the AuthGateway Portal theme disallows any crawling.
enableRobotsTXT = true
# Specify a path to publish the catalogue to (hugo defaults this to `public`).
publishDir = "dist"

[params]
  # List of data collections to load entries from.
  # For each of this a file must exist in the `data/` directory (or custom data path you set).
  # The order of entries in the catalogue is based on this order as well as the order of entries
  # within each data file.
  catalogue = ["catalogue", "non-existing-entry"]

  # An optional description to show in the top bar.
  # If not set this defaults to the site title.
  description = "An example application catalogue"
```

[AuthGateway]: https://github.com/stefano-pogliani/auth-gateway
[Bootstrap framework]: https://getbootstrap.com/
[Hugo]: https://gohugo.io/
