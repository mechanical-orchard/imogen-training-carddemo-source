# CardDemo training copy

This is a training copy of CardDemo, the sample mainframe credit card application. It is used in Mechanical Orchard's Imogen engineer training. It is provided as-is, for training and education only.

It holds a subset of CardDemo: 10 batch jobs and 17 CICS screens, plus every file they use.

This project is not affiliated with, endorsed by, or sponsored by Amazon.com, Inc., Amazon Web Services, or their affiliates. "AWS" and "Amazon" are trademarks of Amazon.com, Inc. or its affiliates.

## Where it came from

- Upstream: [aws-samples/aws-mainframe-modernization-carddemo](https://github.com/aws-samples/aws-mainframe-modernization-carddemo), Copyright Amazon.com, Inc. or its affiliates, licensed under Apache-2.0.
- Copied from Mechanical Orchard's fork [mechanical-orchard/aws-mainframe-modernization-carddemo](https://github.com/mechanical-orchard/aws-mainframe-modernization-carddemo), `main` at `8ec67fd8b153bff0d23f48578e9dc3be1f07a239`.

## Modifications

Mechanical Orchard changed these upstream files. Each one also has a notice in its header.

| File | Change |
|---|---|
| `app/cbl/CBEXPORT.cbl` | The export file's record key is now `EXP-KEY` and its record layout matches the export KSDS definition `KEYS(4 27)`. `RECORDING MODE` removed. |
| `app/cbl/CBIMPORT.cbl` | Same change as `CBEXPORT.cbl`. |
| `app/jcl/CBEXPORT.jcl` | Export KSDS key offset changed from `KEYS(4 28)` to `KEYS(4 27)`. |
| `app/cbl/COCRDLIC.cbl` | Removed a stray line (`I`) after a `MOVE DFHBMPRO` statement. |

Mechanical Orchard also added `README.md`, `NOTICE`, `.mo-parse` (configuration for Mechanical Orchard's code parsing tool), `.gitignore` and `.github/CODEOWNERS`. All other files are unmodified copies of the upstream files.

## What is in scope

- Batch jobs: READACCT, READCARD, READXREF, READCUST, INTCALC, POSTTRAN, TRANREPT, CREASTMT, CBIMPORT, CBEXPORT.
- CICS screens: COSGN00C, COMEN01C, COADM01C, COTRN00C, COTRN01C, COACTVWC, COCRDLIC, COCRDSLC, COUSR00C, CORPT00C, COUSR01C, COUSR02C, COUSR03C, COBIL00C, COCRDUPC, COTRN02C, COACTUPC.

Everything else was kept by following the code from those jobs and screens: `EXEC PGM=`, procs, `CALL`, `COPY`, and mapsets. `app/data` is kept whole, and so are `app/csd/CARDDEMO.CSD` and `app/ctl/REPROCT.ctl`. `app/asm/COBDATFT.asm` is kept because READACCT's program CBACT01C calls it.

## What was left out

- `app/app-authorization-ims-db2-mq`, `app/app-transaction-type-db2`, `app/app-vsam-mq` (the DB2, IMS and MQ extensions)
- `app/asm/MVSWAIT.asm`, `app/maclib`, `app/catlg`, `app/scheduler`
- Programs CBTRN01C and COBSWAIT, copybook UNUSED1Y, and procedure `app/proc/TRANREPT.prc`
- The other 28 JCL members
- `samples/`, `scripts/`, `diagrams/`, `CODE_OF_CONDUCT.md`, `CONTRIBUTING.md`

## License

Licensed under the Apache License, Version 2.0. See [`LICENSE`](LICENSE) and [`NOTICE`](NOTICE). Mechanical Orchard's modifications and additions are also licensed under Apache-2.0. The software is provided "AS IS", without warranties or conditions of any kind.
