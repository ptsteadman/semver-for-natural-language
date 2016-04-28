Semantic Versioning For Natural Language 0.1.0
==============================================

Summary
-------

Given a version number MAJOR.MINOR.PATCH, increment the:

1. MAJOR version when you make changes that affect the meaning of the abstract
   summary of the text,
1. MINOR version when you make changes that affect the meaning of part of the
   text, but do not affect the abstract summary, and
1. PATCH version when you make changes that do not have a significant effect on
   the meaning of the text.

Additional labels for pre-release and metadata are available as extensions to
the MAJOR.MINOR.PATCH format.

Introduction
------------

In the world of writing, whether one is writing essays, novels, or textbooks,
there is no consistent system for versioning texts.  A textbook might have
different editions, but when a book goes from "First Edition" to "Second
Edition", there's no way to know if it was just a few typos that were corrected,
or if the book was almost fully rewritten in order to reflect a paradigm shift
in the field.  Single, flat version numbers can create unnecessary rigidity and
uncertainty.  For example, if other writers have referenced an article without a
version number, the author of the referenced article might be unwilling to make
changes to that article, because people might end up referencing inconsistent
versions of the text.

In creative works, authors often feel that it's necessary to create a final,
crystallized version of the text, even when input after an initial publication
could improve the work.  A standardized semantic versioning system for natural
language could help authors work collaboratively with texts as fluid, living
documents.  An author could specify that they are welcome to patch or minor
level contributions, but are unwilling to chance the general meaning of their work.

Semantic Versioning for Natural Language is a simple set of rules that dictate
how version numbers are assigned and incremented.  For this system to work, you
first need to declare a public abstract for your text.  This public abstract
also serves another important purpose: it makes the text itself more accessible,
indexable, and useful.  Creating a concise, accurate summary of a text is
challenging, but will prove valuable to individuals evaluating whether or not
they want to read the full text.  The abstract can also serve as a roadmap for
your own writing, or contributions from others.  

Once you identify your public abstract, you communicate changes to it with
specific increments to your version number.  Consider a version format of X.Y.Z
(Major.Minor.Patch). Changes that don't significantly affect the meaning of the
text increment the patch version, changes that affect the meaning of the text
but aren't significant enough to effect the public abstract increment the minor
version, and changes that affect the overall meaning of the text and thus the
public abstract increment the major version.

Under this scheme, version numbers and the way they change convey meaning about
the underlying text and what has been modified from one version to the next.

Semantic Versioning for Natural Language is inspired by the Semantic Versioning
system used in the software engineering community to manage dependencies between
different programs.  A description of this system is available
[here](semver.org).

Semantic Versioning for Natural Language Specification (SemVerNL)
------------------------------------------

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD",
"SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be
interpreted as described in [RFC 2119](http://tools.ietf.org/html/rfc2119).

1. Texts using Semantic Versioning for Natural Language MUST declare a public
   abstract. This abstract could be declared in the text itself or exist
   strictly in documentation.  For example, in a novel, the abstract would
   usually be separate from the text, as it would often contain "spoilers".
   However it is done, it should be precise and comprehensive.

1. A normal version number MUST take the form X.Y.Z where X, Y, and Z are
   non-negative integers, and MUST NOT contain leading zeroes. X is the major
   version, Y is the minor version, and Z is the patch version.  Each element
   MUST increase numerically. For instance: 1.9.0 -> 1.10.0 -> 1.11.0.

1. Once a versioned package has been released, the contents of that version MUST
   NOT be modified. Any modifications MUST be released as a new version.

1. Major version zero (0.y.z) is for initial development. Anything may change at
   any time. The public abstract should not be considered stable.

1. Version 1.0.0 defines the public abstract. The way in which the version
   number is incremented after this release is dependent on this abstract
   and how it changes.

1. Patch version Z (x.y.Z | x > 0) MUST be incremented if only changes,
   additions, or deletions are introduced that have negligible semantic
   implications.  

1. Minor version Y (x.Y.z | x > 0) MUST be incremented if semantic changes,
   additions, or deletions are introduced that do not affect the public
   abstract.  It MAY be incremented if substantial stylistic or formatting
   changes are introduced that could affect the text in such a way that the
   meaning is changed.  Patch version MUST be reset to 0 when minor version is
   incremented.

1. Major version X (X.y.z | X > 0) MUST be incremented if any changes,
   additions, or deletions are made that require a change to the public
   abstract. It MAY also include minor and patch level changes. Patch and minor
   version MUST be reset to 0 when major version is incremented.

1. A pre-release version MAY be denoted by appending a hyphen and a series of
   dot separated identifiers immediately following the patch version.
   Identifiers MUST comprise only ASCII alphanumerics and hyphen [0-9A-Za-z-].
   Identifiers MUST NOT be empty. Numeric identifiers MUST NOT include leading
   zeroes. Pre-release versions have a lower precedence than the associated
   normal version. A pre-release version indicates that the version is unstable
   and might not satisfy the intended compatibility requirements as denoted by
   its associated normal version. Examples: 1.0.0-alpha, 1.0.0-alpha.1,
   1.0.0-0.3.7, 1.0.0-x.7.z.92.

1. Build metadata MAY be denoted by appending a plus sign and a series of dot
   separated identifiers immediately following the patch or pre-release version.
   Identifiers MUST comprise only ASCII alphanumerics and hyphen [0-9A-Za-z-].
   Identifiers MUST NOT be empty. Build metadata MUST be ignored when
   determining version precedence. Thus two versions that differ only in the
   build metadata, have the same precedence. Examples: 1.0.0-alpha+001,
   1.0.0+20130313144700, 1.0.0-beta+exp.sha.5114f85.

1. Precedence refers to how versions are compared to each other when ordered.
   Precedence MUST be calculated by separating the version into major, minor,
   patch and pre-release identifiers in that order (Build metadata does not
   figure into precedence). Precedence is determined by the first difference
   when comparing each of these identifiers from left to right as follows:
   Major, minor, and patch versions are always compared numerically. Example:
   1.0.0 < 2.0.0 < 2.1.0 < 2.1.1. When major, minor, and patch are equal, a
   pre-release version has lower precedence than a normal version. Example:
   1.0.0-alpha < 1.0.0. Precedence for two pre-release versions with the same
   major, minor, and patch version MUST be determined by comparing each dot
   separated identifier from left to right until a difference is found as
   follows: identifiers consisting of only digits are compared numerically and
   identifiers with letters or hyphens are compared lexically in ASCII sort
   order. Numeric identifiers always have lower precedence than non-numeric
   identifiers. A larger set of pre-release fields has a higher precedence than
   a smaller set, if all of the preceding identifiers are equal.  Example:
   1.0.0-alpha < 1.0.0-alpha.1 < 1.0.0-alpha.beta < 1.0.0-beta < 1.0.0-beta.2 <
   1.0.0-beta.11 < 1.0.0-rc.1 < 1.0.0.

Backus–Naur Form Grammar for Valid SemVer Versions
--------------------------------------------------

    <valid semver> ::= <version core>
                     | <version core> "-" <pre-release>
                     | <version core> "+" <build>
                     | <version core> "-" <pre-release> "+" <build>

    <version core> ::= <major> "." <minor> "." <patch>

    <major> ::= <numeric identifier>

    <minor> ::= <numeric identifier>

    <patch> ::= <numeric identifier>

    <pre-release> ::= <dot-separated pre-release identifiers>

    <dot-separated pre-release identifiers> ::= <pre-release identifier>
                                              | <pre-release identifier> "." <dot-separated pre-release identifiers>

    <build> ::= <dot-separated build identifiers>

    <dot-separated build identifiers> ::= <build identifier>
                                        | <build identifier> "." <dot-separated build identifiers>

    <pre-release identifier> ::= <alphanumeric identifier>
                               | <numeric identifier>

    <build identifier> ::= <alphanumeric identifier>
                         | <digits>

    <alphanumeric identifier> ::= <non-digit>
                                | <non-digit> <identifier characters>
                                | <identifier characters> <non-digit>
                                | <identifier characters> <non-digit> <identifier characters>

    <numeric identifier> ::= "0"
                           | <positive digit>
                           | <positive digit> <digits>

    <identifier characters> ::= <identifier character>
                              | <identifier character> <identifier characters>

    <identifier character> ::= <digit>
                             | <non-digit>

    <non-digit> ::= <letter>
                  | "-"

    <digits> ::= <digit>
               | <digit> <digits>

    <digit> ::= "0"
              | <positive digit>

    <positive digit> ::= "1" | "2" | "3" | "4" | "5" | "6" | "7" | "8" | "9"

    <letter> ::= "A" | "B" | "C" | "D" | "E" | "F" | "G" | "H" | "I" | "J"
               | "K" | "L" | "M" | "N" | "O" | "P" | "Q" | "R" | "S" | "T"
               | "U" | "V" | "W" | "X" | "Y" | "Z" | "a" | "b" | "c" | "d"
               | "e" | "f" | "g" | "h" | "i" | "j" | "k" | "l" | "m" | "n"
               | "o" | "p" | "q" | "r" | "s" | "t" | "u" | "v" | "w" | "x"
               | "y" | "z"


Why Use Semantic Versioning?
----------------------------

This is not a new or revolutionary idea. In fact, you probably do something
close to this already. The problem is that "close" isn't good enough. Without
compliance to some sort of formal specification, version numbers are essentially
useless for for scholarship, legal purposes, or collaboration.  By giving a name
and clear definition to the above ideas, it becomes easy to communicate your
intentions to the users of your writing.  Once these intentions are clear,
flexible (but not too flexible) specifications can finally be made.

If all of this sounds desirable, all you need to do to start using Semantic
Versioning is to declare that you are doing so and then follow the rules. Link
to this website from your README so others know the rules and can benefit from
them.


FAQ
---

### How should I deal with revisions in the 0.y.z initial development phase?

The simplest thing to do is start your initial development release at 0.1.0
and then increment the minor version for each subsequent release.

### How do I know when to release 1.0.0?

If your writing has been published in a form that implies completeness, it
should probably already be 1.0.0. If you have a stable abstract on which other
writers have come to depend, you should be 1.0.0. If you're worrying a lot about
backwards compatibility, you should probably already be 1.0.0.

### Doesn't this discourage rapid writing and fast iteration?

Major version zero is all about rapid development. If you're changing the
abstract of your work every day you should either still be in version 0.y.z or
on a separate development branch working on the next major version.

### If even the tiniest backwards incompatible changes to the public abstract require a major version bump, won't I end up at version 42.0.0 very rapidly?

This is a question of responsible writing and foresight. Incompatible changes
should not be introduced lightly to writing that is important to other people.
The cost that must be incurred to upgrade can be significant.  Having to bump
major versions to release incompatible changes means you'll think through the
impact of your changes, and evaluate the cost/benefit ratio involved.

### Documenting the entire public abstract is too much work!

It is your responsibility as a professional writer to properly document writing
that is intended to be read by others. Managing complexity is a hugely important
part of what writers do. In the long run, Semantic Versioning, and the
insistence on a well defined public abstract, can keep everyone and everything
running smoothly.

### What do I do if I accidentally release a backwards incompatible change as a minor version?

As soon as you realize that you've broken the Semantic Versioning spec, fix
the problem and release a new minor version that corrects the problem and
restores backwards compatibility. Even under this circumstance, it is
unacceptable to modify versioned releases. If it's appropriate,
document the offending version and inform your users of the problem so that
they are aware of the offending version.


### Does SemVer have a size limit on the version string?

No, but use good judgment. A 255 character version string is probably overkill,
for example. Also, specific systems may impose their own limits on the size of
the string.

### Is "v1.2.3" a semantic version?

No, "v1.2.3" is not a semantic version. However, prefixing a semantic version
with a "v" is a common way (in English) to indicate it is a version number.
Abbreviating "version" as "v" is often seen with version control. Example:
`git tag v1.2.3 -m "Release version 1.2.3"`, in which case "v1.2.3" is a tag
name and the semantic version is "1.2.3".


About
-----

The Semantic Versioning for Natural Language specification is authored by
[Patrick Steadman](https://ptsteadman.com).

If you'd like to leave feedback, please [open an issue on
GitHub](https://github.com/ptsteadman/semver-for-natural-language/issues).


License
-------

Creative Commons - CC BY 3.0
http://creativecommons.org/licenses/by/3.0/
