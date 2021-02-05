# Chapter 1


![](./flow.drawio.svg)

1) Scan QR Code


QR Code information:
```bash
did:iota:123456789abcdefghi
```

Load from tangle (DIDDocument):

Example result
```bash
{
  "@context": "https://www.w3.org/ns/did/v1",
  "id": "did:example:123456789abcdefghi",
  "authentication": [{
    
    "id": "did:example:123456789abcdefghi#keys-1",
    "type": "Ed25519VerificationKey2018", 
    "controller": "did:example:123456789abcdefghi",
    "publicKeyBase58": "H3C2AVvLMv6gmMNam3uVAjZpfkcJCwDwnZn6z3wXmqPV"
  }],
  "service": [{
    
    "id":"did:example:123456789abcdefghi#vcs",
    "type": "DoorService", 
    "serviceEndpoint": "https://example.com/doors/123456789abcdefghi/open"
  }]
}
```


2) Actor Send open Request to Server

curl POST https://example.com/doors/123456789abcdefghi/open --data=did:iota:my_id

Server know who want to access which door.

3) Server acceps request and creates VC and sends back to Actor

4) Actor Signs VC send back to door server

5) Door Server ops Open, if VC is valid. 