# CardDemo training copy

This is a training copy of CardDemo, used by the Imogen engineer certification. Every certification Coder workspace clones it. It is shared by all trainees and read-only for them.

It holds only the part of CardDemo that [`aws-carddemo-java`](https://github.com/mechanical-orchard/aws-carddemo-java) modernizes with its cold-start pipelines: 10 batch jobs and 17 CICS screens, plus every file they use.

## Where it came from

- Upstream: [aws-samples/aws-mainframe-modernization-carddemo](https://github.com/aws-samples/aws-mainframe-modernization-carddemo) (Apache-2.0; see `LICENSE` and `NOTICE`).
- Copied from the fork [mechanical-orchard/aws-mainframe-modernization-carddemo](https://github.com/mechanical-orchard/aws-mainframe-modernization-carddemo), `main` at `8ec67fd8b153bff0d23f48578e9dc3be1f07a239`.

## What is in scope

The two scope lists in `aws-carddemo-java`:

- `docs/skills/cold-start-core-batch-jobs/SKILL.md`: READACCT, READCARD, READXREF, READCUST, INTCALC, POSTTRAN, TRANREPT, CREASTMT, CBIMPORT, CBEXPORT.
- `docs/skills/cold-start-core-screens/SKILL.md`: COSGN00C, COMEN01C, COADM01C, COTRN00C, COTRN01C, COACTVWC, COCRDLIC, COCRDSLC, COUSR00C, CORPT00C, COUSR01C, COUSR02C, COUSR03C, COBIL00C, COCRDUPC, COTRN02C, COACTUPC.

Everything else was kept by following the code from those jobs and screens: `EXEC PGM=`, procs, `CALL`, `COPY`, and mapsets. `app/data` is kept whole, and so are `app/csd/CARDDEMO.CSD` and `app/ctl/REPROCT.ctl`. `app/asm/COBDATFT.asm` is kept because READACCT's program CBACT01C calls it.

## What was left out

- `app/app-authorization-ims-db2-mq`, `app/app-transaction-type-db2`, `app/app-vsam-mq` (the DB2, IMS and MQ extensions)
- `app/asm/MVSWAIT.asm`, `app/maclib`, `app/catlg`, `app/scheduler`
- Programs CBTRN01C and COBSWAIT, copybook UNUSED1Y, and procedure `app/proc/TRANREPT.prc`
- The other 28 JCL members
- `samples/`, `scripts/`, `diagrams/`, `CODE_OF_CONDUCT.md`, `CONTRIBUTING.md`

Tracked in Momentum as MT-2575.
