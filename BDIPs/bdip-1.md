# BDIP-1

---
bdip: 1
title: BDIP Purpose and Guidelines
author: Shun Usami <usatie@yenom.tech> and others
type: Meta
status: Draft
created: 2018-11-01
---


## What is a BDIP?

BDIP stands for Bitcoin DApps Improvement Proposal. A BDIP is a design document providing information to the Bitcoin DApps community, or describing a new feature for Bitcoin DApps or its processes or environment. The BDIP should provide a concise technical specification of the feature and a rationale for the feature. The BDIP author is responsible for building consensus within the community and documenting dissenting opinions.

## BDIP Rationale

We intend BDIPs to be the primary mechanisms for proposing new features, for collecting community technical input on an issue, and for documenting the design decisions that have gone into Bitcoin DApps. Because the BDIPs are maintained as text files in a versioned repository, their revision history is the historical record of the feature proposal.

For Bitcoin DApps implementers, BDIPs are a convenient way to track the progress of their implementation. Ideally each implementation maintainer would list the BDIPs that they have implemented. This will give end users a convenient way to know the current status of a given implementation or library.

## BDIP Types

There are three types of BDIP:

- A **Standard Track BDIP** describes any change that affects most or all Bitcoin DApps implementations. 
- An **Informational BDIP** describes an Bitcoin DApps design issue, or provides general guidelines or information to the Bitcoin DApps community, but does not propose a new feature. Informational BDIPs do not necessarily represent Bitcoin DApps community consensus or a recommendation, so users and implementers are free to ignore Informational BDIPs or follow their advice.
- A **Meta BDIP** describes a process surrounding Bitcoin DApps or proposes a change to (or an event in) a process.

It is highly recommended that a single BDIP contain a single key proposal or new idea. The more focused the BDIP, the more successful it tends to be. A change to one client doesn't require an BDIP; a change that affects multiple clients, or defines a standard for multiple apps to use, does.

A BDIP must meet certain minimum criteria. It must be a clear and complete description of the proposed enhancement. The enhancement must represent a net improvement. The proposed implementation, if applicable, must be solid and must not complicate the protocol unduly.


## BDIP Work Flow

Parties involved in the process are you, the champion or *BDIP author*, the [*BDIP editors*](#bdip-editors).

:warning: Before you begin, vet your idea, this will save you time. Ask the Bitcoin DApps community first if an idea is original to avoid wasting time on something that will be be rejected based on prior research (searching the Internet does not always do the trick). It also helps to make sure the idea is applicable to the entire community and not just the author. Just because an idea sounds good to the author does not mean it will work for most people in most areas where Bitcion DApps are used. Examples of appropriate public forums to gauge interest around your BDIP include [the Bitcoin subreddit] and [the Issues section of this repository]. In particular, [the Issues section of this repository] is an excellent place to discuss your proposal with the community and start creating more formalized language around your BDIP.

Your role as the champion is to write the BDIP using the style and format described below, shepherd the discussions in the appropriate forums, and build community consensus around the idea. Following is the process that a successful BDIP will move along:

```
[ WIP ] -> [ DRAFT ] -> [ LAST CALL ] -> [ ACCEPTED ] -> [ FINAL ]
```

Each status change is requested by the BDIP author and reviewed by the BDIP editors. Use a pull request to update the status. Please include a link to where people should continue discussing your BDIP. The BDIP editors will process these requests as per the conditions below.

* **Active** -- Some Informational and Meta BDIPs may also have a status of “Active” if they are never meant to be completed. E.g. BDIP 1 (this BDIP).
* **Work in progress (WIP)** -- Once the champion has asked the Bitcoin DApps community whether an idea has any chance of support, they will write a draft EIP as a [pull request]. Consider including an implementation if this will aid people in studying the BDIP.
  * :arrow_right: Draft -- If agreeable, BDIP editor will assign the BDIP a number (generally the issue or PR number related to the BDIP) and merge your pull request. The BDIP editor will not unreasonably deny an BDIP.
  * :x: Draft -- Reasons for denying draft status include being too unfocused, too broad, duplication of effort, being technically unsound, not providing proper motivation or addressing backwards compatibility.
* **Draft** -- Once the first draft has been merged, you may submit follow-up pull requests with further changes to your draft until such point as you believe the BDIP to be mature and ready to proceed to the next status. An BDIP in draft status must be implemented to be considered for promotion to the next status.
  * :arrow_right: Last Call -- If agreeable, the BDIP editor will assign Last Call status and set a review end date (`review-period-end`), normally 14 days later.
  * :x: Last Call -- A request for Last Call status will be denied if material changes are still expected to be made to the draft.
* **Last Call** -- This BDIP will be listed prominently on the https://bdip.web3bch.cash/ website.
  * :x: -- A Last Call which results in material changes or substantial unaddressed technical complaints will cause the BDIP to revert to Draft.
  * :arrow_right: Final -- A successful Last Call without material changes or unaddressed technical complaints will become Final.
* **Final** -- This BDIP represents the current state-of-the-art. A Final BDIP should only be updated to correct errata.

Other exceptional statuses include:

* **Rejected** -- A BDIP that is fundamentally broken.
* **Superseded** -- A BDIP which was previously final but is no longer considered state-of-the-art. Another BDIP will be in Final status and reference the Superseded BDIP.

## What belongs in a successful BDIP?

Each BDIP should have the following parts:

- **Preamble** - RFC 822 style headers containing metadata about the BDIP, including the BDIP number, a short descriptive title (limited to a maximum of 44 characters), and the author details. See [below](https://github.com/web3bch/BDIPs/blob/master/BDIPs/bdip-1.md#bdip-header-preamble) for details.
- **Simple Summary** - “If you can’t explain it simply, you don’t understand it well enough.” Provide a simplified and layman-accessible explanation of the BDIP.
- **Abstract** - a short (~200 word) description of the technical issue being addressed.
- **Motivation (optional)** - The motivation is critical for BDIPs. It should clearly explain why the existing protocol specification is inadequate to address the problem that the BDIP solves. BDIP submissions without sufficient motivation may be rejected outright.
- **Specification** - The technical specification should describe the syntax and semantics of any new feature. The specification should be detailed enough to allow competing, interoperable implementations.
- **Rationale** - The rationale fleshes out the specification by describing what motivated the design and why particular design decisions were made. It should describe alternate designs that were considered and related work, e.g. how the feature is supported in other languages. The rationale may also provide evidence of consensus within the community, and should discuss important objections or concerns raised during discussion.
- **Backwards Compatibility** - All BDIPs that introduce backwards incompatibilities must include a section describing these incompatibilities and their severity. The BDIP must explain how the author proposes to deal with these incompatibilities. BDIP submissions without a sufficient backwards compatibility treatise may be rejected outright.
- **Test Cases** - Test cases for an implementation are mandatory for BDIPs that are affecting consensus changes. Other BDIPs can choose to include links to test cases if applicable.
- **Implementations** - The implementations must be completed before any BDIP is given status “Final”, but it need not be completed before the BDIP is merged as draft. While there is merit to the approach of reaching consensus on the specification and rationale before writing code, the principle of “rough consensus and running code” is still useful when it comes to resolving many discussions of API details.
- **Copyright Waiver** - All BDIPs must be in the public domain. See the bottom of this BDIP for an example copyright waiver.

## BDIP Header Preamble

Each BDIP must begin with an RFC 822 style header preamble, preceded and followed by three hyphens (`---`). The headers must appear in the following order. Headers marked with "*" are optional and are described below. All other headers are required.

| Header title | Header format|
|:-----------:|:------------|
| bdip: | <BDIP number> (this is determined by the BDIP editor) |
| title: | <BDIP title> (limited to maximum of 44 characters) |
| author: | <a list of the author's or authors' name(s) and/or username(s), or name(s) and email(s). Details are below.> |
| * discussions-to: | \<a url pointing to the official discussion thread\> <br> :x: `discussions-to` can not be a Github `Pull-Request`. |
| status: | <`Draft` \| `Last Call` \| `Final` \| `Active` \| `Deferred` \| `Rejected` \| `Superseded`> |
|* review-period-end:| YYYY-MM-DD |
| type:| <`Standards Track` \| `Informational` \| `Meta`> |
| * category:| <`Core` \| `Wallet` \| `Application`> |
| created:| <date created on, in ISO 8601 (yyyy-mm-dd) format> |
| * requires:| <BDIP number(s)> |
| * replaces:| <BDIP number(s)> |
| * superseded-by:| <BDIP number(s)> |
| * resolution:| \<a url pointing to the resolution of this BDIP\> |
  
Headers that permit lists must separate elements with commas.

### Author header

The author header optionally lists the names, email addresses or usernames of the authors/owners of the BDIP. Those who prefer anonymity may use a username only, or a first name and a username. The format of the author header value must be:

Random J. User &lt;address@dom.ain&gt;

or

Random J. User (@username)

if the email address or GitHub username is included, and

Random J. User

if the email address is not given.


### Discussions-to header
While a BDIP is a draft, a discussions-to header will indicate the mailing list or URL where the BDIP is being discussed. As mentioned above, examples for places to discuss your BDIP including an issue in this repo or in a fork of this repo, and [Reddit r/bitcoin](https://www.reddit.com/r/bitcoin/). No discussions-to header is necessary if the BDIP is being discussed privately with the author.

### Type header
The type header specifies the type of BDIP: Standards Track, Meta, or Informational.

### Category header
The category header specifies the BDIP's category. This is required for standards-track BDIPs only.

### Created header
The created header records the date that the BDIP was assigned a number. Both headers should be in yyyy-mm-dd format, e.g. 2001-08-14.

### Requires header
BDIPs may have a requires header, indicating the BDIP numbers that this BDIP depends on.

### Superseded-by header
BDIPs may also have a superseded-by header indicating that an BDIP has been rendered obsolete by a later document; the value is the number of the BDIP that replaces the current document. The newer BDIP must have a Replaces header containing the number of the BDIP that it rendered obsolete.

### Resolution header
The resolution header is required for Standards Track BDIPs only. It contains a URL that should point to an email message or other web resource where the pronouncement about the BDIP is made.

## Auxiliary Files

BDIPs may include auxiliary files such as diagrams. Such files must be named BDIP-XXXX-Y.ext, where “XXXX” is the BDIP number, “Y” is a serial number (starting at 1), and “ext” is replaced by the actual file extension (e.g. “png”).

## Transferring BDIP Ownership

It occasionally becomes necessary to transfer ownership of BDIPs to a new champion. In general, we'd like to retain the original author as a co-author of the transferred BDIP, but that's really up to the original author. A good reason to transfer ownership is because the original author no longer has the time or interest in updating it or following through with the BDIP process, or has fallen off the face of the 'net (i.e. is unreachable or isn't responding to email). A bad reason to transfer ownership is because you don't agree with the direction of the BDIP. We try to build consensus around an BDIP, but if that's not possible, you can always submit a competing BDIP.

If you are interested in assuming ownership of an BDIP, send a message asking to take over, addressed to both the original author and the BDIP editor. If the original author doesn't respond to email in a timely manner, the BDIP editor will make a unilateral decision (it's not like such decisions can't be reversed :)).

## BDIP Editors

The current BDIP editors are

` * Shun Usami (@usatie)`

` * Taiki Uchida (@yuiki)`

` * Akifuji Fujita (@akifuj)`

` * Gabriel Cardona (@cgcardona).`

` * SpendBCH (@SpendBCH).`

## BDIP Editor Responsibilities

For each new BDIP that comes in, an editor does the following:

- Read the BDIP to check if it is ready: sound and complete. The ideas must make technical sense, even if they don't seem likely to get to final status.
- The title should accurately describe the content.
- Check the BDIP for language (spelling, grammar, sentence structure, etc.), markup (Github flavored Markdown), code style

If the BDIP isn't ready, the editor will send it back to the author for revision, with specific instructions.

Once the BDIP is ready for the repository, the BDIP editor will:

- Assign an BDIP number (generally the PR number or, if preferred by the author, the Issue # if there was discussion in the Issues section of this repository about this BDIP)

- Merge the corresponding pull request

- Send a message back to the BDIP author with the next step.

The BDIP editors monitor BDIP changes, and correct any structure, grammar, spelling, or markup mistakes we see.

The editors don't pass judgment on BDIPs. We merely do the administrative & editorial part.

## History

This document was derived heavily from [Ethereum's EIP-1] written by Martin Becze, Hudson Jameson, and others, which in turn was drived from [Bitcoin's BIP-0001] written by Amir Taaki, which in turn was derived from [Python's PEP-0001]. In many places text was simply copied and modified. Although the PEP-0001 text was written by Barry Warsaw, Jeremy Hylton, and David Goodger, they are not responsible for its use in the Bitcoin DApps Improvement Process, and should not be bothered with technical questions specific to Bitcoin DApps or the BDIP. Please direct all comments to the BDIP editors.

Nov 1, 2018: BDIP 1 was made.

See [the revision history for further details](https://github.com/web3bch/BDIPs/commits/master/BDIPs/bdip-1.md), which is also available by clicking on the History button in the top right of the BDIP.

### Bibliography

[the Bitcoin subreddit]: https://www.reddit.com/r/bitcoin/
[pull request]: https://github.com/web3bch/BDIPs/pulls
[the Issues section of this repository]: https://github.com/web3bch/BDIPs/issues
[markdown]: https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet
[Ethereum's EIP-1]: https://eips.ethereum.org/EIPS/eip-1
[Bitcoin's BIP-0001]: https://github.com/bitcoin/bips
[Python's PEP-0001]: https://www.python.org/dev/peps/

## Copyright

Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
