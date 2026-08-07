# Registry Hive (`registry-hive`)

**Category:** forensics · **Difficulty:** medium · **Points:** 250

A Windows registry hive hides the key in a persistence value.

## Run it

```bash
docker build -t picoclone/registry-hive .
# `picoclone start registry-hive` (or the web UI) prints the docker run line with your
# PICOCLONE_SERVER + PICOCLONE_INSTANCE_TOKEN
```

## Recover the flag

The delivery blob is XOR-encrypted then base64-encoded. Discover the challenge key, then invert XOR+base64.

The plaintext flag is never written to disk or served — only the encoded delivery blob
is. When you have it:

```bash
picoclone submit registry-hive 'picoclone{...}'
```

## Hints

- Persistence often lives under Run keys.
- Parse the hive and read the suspicious value.
