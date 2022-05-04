# Marvel API Postman Worksplace

[![Run in Postman](https://run.pstmn.io/button.svg)](https://god.gw.postman.com/run-collection/11320063-5d70d457-7b01-4587-8733-de2b5eef7083?action=collection%2Ffork&collection-url=entityId%3D11320063-5d70d457-7b01-4587-8733-de2b5eef7083%26entityType%3Dcollection%26workspaceId%3Df6b2b9e3-9c34-415d-8cbe-3eea7e9a73c7)

## General API information

**The Marvel Comics API** is a RESTful service which provides methods of accessing specific resources at canonical URLs and for searching and filtering sets of resources by various criteria.

**All representations are encoded as JSON objects.**

## Service endpoint

The Marvel Comics API's base endpoint is `http://gateway.marvel.com/`.

## Authentication

*This workspace already has the authentication set-up to work with each entity, please refer to the Pre-request Script included in this workspace*

Server-side applications must pass two parameters in addition to the `apikey` parameter:

*   **ts** - a timestamp (or other long strumg which can change on a request-by-request basis)
*   **hash** — a md5 digest of the `ts` parameter, your private key and your public key (e.g, `md5`(`ts`+`privateKey`+`publicKey`)
    

*For example*, a user with a public key of `1234` and a private key of `abcd` could construct a valid call as follows:

`http://gateway.marvel.com/v1/public/comics?ts=1&apikey=1234&hash=ffd275c5130566a2916217b101f26150`

## Authorization Errors

The following errors are returned by the Marvel Comics API when issues with authorization occur.

These errors are returned by all endpoints.

| **Error Code** | **Error Message** | **Reason for occurring** |
| --- | --- | --- |
| **409** | Missing API Key | Occurs when `apikey` parameter is not included with a request. |
| **409** | Missing Hash | Occurs when `apikey` parameter is included with a request, a `ts` parameter is present, but no `hash` parameter is sent. |
| **409** | Missing timestamp | Occurs when `ts` parameter is sent when `apikey` and `hash` parameter are present. |
| **401** | Invalid Referrer | Occurs when a referrer which is not valid for the passed `apikey` parameter is sent. |
| **401** | Invalid Hash | Occurs when a `ts`, `hash` and `apikey` parameter are sent but the `hash` is not valid per the above `hash` generation rule. |
| **405** | Method Not Allowed | Occurs when an API endpoint is accessed using a HTTP verb which is not allowed for that endpoint. |
| **403** | Forbidden | Occurs when a user with an otherwise authenticated request attempts to access an endpoint which they do not have access. |

## Resources

You can access *six resources types* using the API:

*   **Comics**: Individual print and digital comic issues, collections and graphic novels. For example: **Amazing Fantasy #15**.
*   **Series**: Sequentially numbered (well, mostly sequentially numbered) group comics with the same title. For example: **Uncanny X-Men**.
*   **Stories**: Indivisible, reusable components of comics. For example, the cover from Amazing Fantasy #15 or the origin of Spider-Man story from that comic.
*   **Creators**: Women, men and organizations who create comics. For example: *Jack Kirby*
*   **Characters**: The women, men, organizations, alien species, deities, animals, non-corporeal entities, trans-dimensional manifestations, abstract personifications, and green amorphous blobs which occupy the Marvel Universe (and various alternate universes, timelines and altered realities therein). For example, **Spider-Man**.
