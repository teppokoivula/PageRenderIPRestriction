Page Render IP Restriction Module
=================================

This module adds basic IP restriction capabilities to page rendering. Please note
that this is only meant to be used as an additional security measure in addition
to typical username/password authentication or something similar, not on it's
own.

This is very important especially if protected content is valuable and/or sensitive.
In those cases it would also be a much better idea to add all IP restriction rules
within (software or hardware) firewall instead of relying on a module.

## Installing

Copy PageRenderIPRestriction folder to your /site/modules/, go to Admin > Modules,
hit "Check for new modules" and install Page Render IP Restriction. That's it.

## How to use

Default settings for this module don't introduce any restrictions. You should edit
module settings (Admin > Modules > Page Render IP Restriction) to include those IPs
you wish to allow access to your site for. Please note that if you fill in at least
one IP address and check both "Restrict admin access" and "Restrict access for
authenticated users" checkboxes _you will no longer be able to reach Admin
without valid IP_.

Since module version 0.9.0 it is possible to specifically set a list of blocked IPs.
If blocked IPs are defined, only users with one of these IP addresses are prevented
from accessing the site.

## Settings

**Allowed IPs**

* IP addresses that have access to your site
* Each address on its own line
* Supported formats: 127.0.0.1 (individual IPs), 127.0.0.1-127.0.0.255 (IP ranges)
  and 127.0.0.0/24 (CIDR)
* Default: null

**Blocked IPs**

* IP addresses that should not get access to your site
* Each address on its own line
* Supported formats: 127.0.0.1 (individual IPs), 127.0.0.1-127.0.0.255 (IP ranges)
  and 127.0.0.0/24 (CIDR)
* Default: null

**Use client headers when checking IP**

* Trust client headers when IP address is checked
* This option may be required in case your site is behind a proxy or firewall
* Default: false

**Access denied message**

* What message should users get when they're being denied access?
* Leave blank to show no message. HTML markup is supported.
* Default: null

**Access denied action**

* What should happen when user is denied access?
* Possible values: "Exit with specified message" or "Redirect user to login page",
  but latter option has no effect if admin access is also restricted
* Default: null (send HTTP/1.1 403 Forbidden header + no message)

**Restrict admin access**

* If you check this box, admin pages will only be available for users with valid IPs
* Default: false

**Restrict access for authenticated users**

* If you check this box, IP restriction will also apply to authenticated (logged in)
  users.
* Default: false

**Exceptions to access restriction (allowed paths)**

* With this setting you can define paths that are excluded from access restriction
* You can optionally specify the request method: /my-allowed-url/ POST
* Default: null

**Exceptions to access restriction (allowed domains)**

* With this setting you can define domains that are excluded from access restriction
* Default: null