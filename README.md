Viacoin Core integration/staging tree
=====================================

[![Build Status](https://travis-ci.org/romanornr/viacoin.svg?branch=master)](https://travis-ci.org/romanornr/viacoin)

https://viacoin.org

What is Viacoin?
----------------

Viacoin is an experimental digital currency that enables instant payments to
anyone, anywhere in the world. Viacoin uses peer-to-peer technology to operate
with no central authority: managing transactions and issuing money are carried
out collectively by the network. Viacoin Core is the name of open source
software which enables the use of this currency.

For more information, as well as an immediately useable, binary version of
the Viacoin Core software, see https://viacoin.org

License
-------

Viacoin Core is released under the terms of the MIT license. See [COPYING](COPYING) for more
information or see https://opensource.org/licenses/MIT.

Development Process
-------------------

The `master` branch is regularly built and tested, but is not guaranteed to be
completely stable. [Tags](https://github.com/viacoini/viacoin/tags) are created
regularly to indicate new official, stable release versions of Viacoin Core.

The contribution workflow is described in [CONTRIBUTING.md](CONTRIBUTING.md).

The developer [mailing list](https://groups.google.com/forum/#!forum/viacoin-development)
should be used to discuss complicated or controversial changes before working
on a patch set.

Testing
-------

Testing and code review is the bottleneck for development; we get more pull
requests than we can review and test on short notice. Please be patient and help out by testing
other people's pull requests, and remember this is a security-critical project where any mistake might cost people
lots of money.

### Automated Testing

Developers are strongly encouraged to write [unit tests](/doc/unit-tests.md) for new code, and to
submit new unit tests for old code. Unit tests can be compiled and run
(assuming they weren't disabled in configure) with: `make check`

There are also [regression and integration tests](/qa) of the RPC interface, written
in Python, that are run automatically on the build server.
These tests can be run (if the [test dependencies](/qa) are installed) with: `qa/pull-tester/rpc-tests.py`

The Travis CI system makes sure that every pull request is built for Windows, Linux, and OS X, and that unit/sanity tests are run automatically.

### Manual Quality Assurance (QA) Testing

Changes should be tested by somebody other than the developer who wrote the
code. This is especially important for large or high-risk changes. It is useful
to add a test plan to the pull request description if testing the changes is
not straightforward.

See https://github.com/viacoin/QA/ for how to create a test plan.

Translations
------------

Changes to translations as well as new translations can be submitted to
[Viacoin Core's Transifex page](https://www.transifex.com/projects/p/viacoin/).

Translations are periodically pulled from Transifex and merged into the git repository. See the
[translation process](doc/translation_process.md) for details on how this works.

**Important**: We do not accept translation changes as GitHub pull requests because the next
pull from Transifex would automatically overwrite them again.

DEBUG-LOCKORDER
---------------
Viacoin Core is a multithreaded application, and deadlocks or other multithreading bugs.
can be very difficult to track down. Compiling with -DDEBUG_LOCKORDER (configure CXXFLAGS="-DDEBUG_LOCKORDER -g")
inserts run-time checks to keep track of what locksare held, and adds warning to the debug.log file if inconsistencies are detected.
