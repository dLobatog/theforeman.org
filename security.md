---
layout: default
title: Security
---

## Security process

We take security issues seriously and welcome responsible disclosure from researchers discovering vulnerabilities in Foreman.  Please email [foreman-security@googlegroups.com](mailto:foreman-security@googlegroups.com) (a private address for the security team) with all reports.

We will endeavour to resolve high severity issues in the current stable release and lower severity issues in the next major release.  Announcements of security issues will be made on [foreman-announce](https://groups.google.com/forum/#!forum/foreman-announce) when a release containing a fix is available to end users and credit will be given to the researcher if desired.

## Security advisories

All security advisories made for Foreman are listed below with their corresponding [CVE identifier](http://cve.mitre.org/).

* [CVE-2013-4386: SQL injection in host/host group parameter overrides](security.html#2013-4386)
* [CVE-2013-4182: hosts API privilege escalation](security.html#2013-4182)
* [CVE-2013-4180: DoS via hosts controller input conversion](security.html#2013-4180)
* [CVE-2013-2121: bookmarks remote code execution](security.html#2013-2121)
* [CVE-2013-2113: admin user creation, privilege escalation](security.html#2013-2113)
* [CVE-2013-0210: Arbitrary command execution risk in Foreman proxy](security.html#2013-0210)
* [CVE-2013-0187: XMLHttpRequest bypasses authorization](security.html#2013-0187)
* [CVE-2013-0174: exposed hashed root passwords can be retrieved by unauthenticated remote users](security.html#2013-0174)
* [CVE-2013-0173: insecure fixed salt "foreman" for passwords](security.html#2013-0173)
* [CVE-2013-0171: import allows unauthenticated YAML uploads/parsing leading to arbitrary code execution](security.html#2013-0171)
* [CVE-2012-5648: SQL injection through search mechanism](security.html#2012-5648)
* [CVE-2012-5477: world writable files in proxy](security.html#2012-5477)

### Disclosure details

#### <a id="2013-4386"></a>CVE-2013-4386: SQL injection in host/host group parameter overrides

Host and host group parameter overrides (lookup_values) allowed SQL injection from the host FQDN or host group label.

* Fix released in Foreman 1.2.3
* Redmine issue [#3160](http://projects.theforeman.org/issues/3160)
* Red Hat Bugzilla [#1013076](https://bugzilla.redhat.com/show_bug.cgi?id=CVE-2013-4386)

#### <a id="2013-4182"></a>CVE-2013-4182: hosts API privilege escalation

The /api/hosts API was found to provide access to all hosts without checking whether the current user has privileges to view a particular host.

Thanks to Daniel Lobato of CERN IT-PES-PS for discovering this issue.

* Fix released in Foreman 1.2.2
* Redmine issue [#2863](http://projects.theforeman.org/issues/2863)
* Red Hat Bugzilla [#990374](https://bugzilla.redhat.com/show_bug.cgi?id=CVE-2013-4182)

#### <a id="2013-4180"></a>CVE-2013-4180: DoS via hosts controller input conversion

Power and IPMI boot actions converted user input to symbols, which could lead to memory exhaustion.

Thanks to Marek Hulan of the Red Hat Foreman Team for discovering this issue.

* Fix released in Foreman 1.2.2
* Redmine issue [#2860](http://projects.theforeman.org/issues/2860)
* Red Hat Bugzilla [#989755](https://bugzilla.redhat.com/show_bug.cgi?id=CVE-2013-4180)

#### <a id="2013-2121"></a>CVE-2013-2121: bookmarks remote code execution

Bookmarks could be created in Foreman containing data that was later executed arbitrarily when reading the bookmark.

Thanks to Ramon de C Valle of the Red Hat Product Security Team for discovering this issue.

* Fix released in Foreman 1.2.0
* Redmine issue [#2631](http://projects.theforeman.org/issues/2631)
* Red Hat Bugzilla [#968166](https://bugzilla.redhat.com/show_bug.cgi?id=CVE-2013-2121)

#### <a id="2013-2113"></a>CVE-2013-2113: admin user creation, privilege escalation

Non-admin user with permissions to create or edit other users were able to change the admin flag, or assign roles that they themselves do not have, enabling a privilege escalation.

Thanks to Ramon de C Valle of the Red Hat Product Security Team for discovering this issue.

* Fix released in Foreman 1.2.0
* Redmine issue [#2630](http://projects.theforeman.org/issues/2630)
* Red Hat Bugzilla [#966804](https://bugzilla.redhat.com/show_bug.cgi?id=CVE-2013-2113)

#### <a id="2013-0210"></a>CVE-2013-0210: Arbitrary command execution risk in smart proxy

Requests to the smart proxy Puppet run API were not properly escaped when running the Puppet command, leading to possible arbitrary command execution.

* Fix released in Foreman 1.2.0

#### <a id="2013-0187"></a>CVE-2013-0187: XMLHttpRequest bypasses authorization

XMLHttpRequest or AJAX requests to Foreman were not subject to authorization checks, enabling privilege escalation for authenticated users.

* Fix released in Foreman 1.1

#### <a id="2013-0174"></a>CVE-2013-0174: exposed hashed root passwords can be retrieved by unauthenticated remote users

The external node classifier (ENC) API in Foreman was accessible to any remote host and the output would contain the hashed root psasword (used for unattended installation).  Authentication and authorization features were added to the ENC API to secure this data.

Thanks to Andreas Rogge for discovering this issue.

* Fix released in Foreman 1.1
* Redmine issue [#2069](http://projects.theforeman.org/issues/2069)

#### <a id="2013-0173"></a>CVE-2013-0173: insecure fixed salt "foreman" for passwords

The salt used to hash root passwords (used for unattended installation) was fixed to the string "foreman" instead of being randomized.

* Fix released in Foreman 1.1
* Redmine issue [#2069](http://projects.theforeman.org/issues/2069)

#### <a id="2013-0171"></a>CVE-2013-0171: import allows unauthenticated YAML uploads/parsing leading to arbitrary code execution

Fact and report import APIs in Foreman were accessible to any remote host and accepted YAML input, allowing arbitrary objects to be created on the Foreman server via YAML.  Authentication and authorization features were added to the import APIs to prevent this.

* Fix released in Foreman 1.1
* Redmine issue [#2121](http://projects.theforeman.org/issues/2121)

#### <a id="2012-5648"></a>CVE-2012-5648: SQL injection through search mechanism

Input to the search mechanism in Foreman was not escaped when constructing queries, enabling SQL injection into the resulting query.

* Fix released in Foreman 1.0.2

#### <a id="2012-5477"></a>CVE-2012-5477: world writable files in smart proxy

The smart proxy daemon ran with a umask of 0, causing files and directories written by it to have world-writable bits set.  Files managed by the smart proxy could be modified by local users on the same host.

* Fix released in Foreman 1.1
* Redmine issue [#1929](http://projects.theforeman.org/issues/1929)
