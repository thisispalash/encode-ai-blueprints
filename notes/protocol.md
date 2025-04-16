# Privacy Preserving OCR Network

The following document outlines the deployed protocol on Filecoin that is privacy preserving and 
the rationales behind choices made. There are two types of parties in this network, the (regular)
user and ocr-worker.

### Why does this exist?

## Basic flow
1. user creates boxes somehow (either automated and then confirmed, or actual drawings)
2. these boxes are converted to standard shapes, later step (show with dotted box)
3. encrypts with own private key, and sends encryption, public key, some metadata about shape or number of boxes, size of download, etc. to central contract (likely filecoin, using fevm, do u know about nuances of fevm?)
4. contract emits job-added event
5. some node is watching for events and is thus notified of new job
6. node pulls, decrypts image using provided public key, performs ocr
7. node then encrypts ocr result with provided public key, and sends to central contract along with job_id
8. contract emits job-completed event
9. user pulls data back from contract by providing their secret and nullifer.. okay, this part not sure yet.. how exactly did tornado work? how does the zk come in? im guessing zk here so secret is not actually revealed.. but not sure of zk algos, might just fork tornado or something..

10. after all jobs are completed associated with the receipt, user recombines outputs and gets final ocr-ed output.. 
11. user confirms and stores on local machine, along with original full image.. this pair will be used later to train onchain model.. but again, different process, much later..

## Rate Limiting Nullifiers

### Monetisation

## FVM 

### DataDAO

### Aggregation