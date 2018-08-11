---
title: "Content Identifiers (CIDs)"
menu:
    guides:
        parent: concepts
---

A *content identifier*, or CID, is a label used for addressing content in IPFS. Any correctly-formed CID identifies a specific piece of content, based on that content's cryptographic hash - a different piece of content will have a different hash and will produce different CID's.

Any CID can take a few different forms, each easy for humans and/or software to decode.  Any specific CID can be transformed to other equivalent CID representations (for example, using different base, CID version or codec).  

CID v1 and later are comprised of some leading identifiers making it easy to identify which representation is used, along with the content-hash itself. In v1 and later, these include a multibase identifier, [multicodec](https://github.com/multiformats/multicodec) identifier, and CID version-identifier:

 * The multibase identifier specifies the encoding being used for the CID
 * The CID identifer indicates which version of CID is encoded
 * The multicodec identifier indicates the format of the target content - it helps people and software to know how to interpret that content after the content is fetched

These leading identifiers provide support for different formats to be used in future versions.  Older CIDs have a different design that omits these identifiers — see [version 0](#version-0) below.

Using the first few bytes of the CID, the CID can easily be interpreted; the content can be fetched from IPFS, then decoded with the correct codec. For more details, check out the [CID specification](https://github.com/ipld/cid).  It includes a [decoding algorithm](https://github.com/ipld/cid/blob/ef1b2002394b15b1e6c26c30545fd485f2c4c138/README.md#decoding-algorithm) and links to existing software implementations for decoding CID's.

You might also want to check out the [CID inspector](http://cid-utils.ipfs.team/#zb2rhiVd5G2DSpnbYtty8NhYHeDvNkPxjSqA7YbDPuhdihj9L) for an interactive breakdown of differently-formatted CIDs.

## Version 1

Version 1 is the latest version of CID. It is used by default for `files` ([MFS](/concepts/mfs)) and `object` operations.

## Version 0

When IPFS was first designed, we specified the consistent use of base 58-encoded multihashes as the content identifiers.  While this is s simpler, it is also much less flexible than newer CIDs.  CIDv0 is still used by default when adding files and blocks to IPFS, so you should generally try to support them.

There is a [decoding algorithm](https://github.com/ipld/cid/blob/ef1b2002394b15b1e6c26c30545fd485f2c4c138/README.md#decoding-algorithm) that shows how you can distinguish CID v0 from newer versions.
