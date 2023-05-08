# Trivy Demo

[![Trivy scanning](https://github.com/fredrkl/trivy-demo/actions/workflows/trivy-scan.yaml/badge.svg)](https://github.com/fredrkl/trivy-demo/actions/workflows/trivy-scan.yaml)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Demo repository showcasing some of the possibilities of Aqua Trivy.

![Trivy](./images/Aqua-trivy-logo.png)

## Image scanning

Let's look at an example of scanning an image using Trivy:

```bash
> trivy image python:3.4-alpine
```

### Output

<details>
    <summary>The output:</summary>

```text
2023-05-06T15:29:29.058Z        INFO    Need to update DB
2023-05-06T15:29:29.058Z        INFO    DB Repository: ghcr.io/aquasecurity/trivy-db
2023-05-06T15:29:29.058Z        INFO    Downloading DB...
36.61 MiB / 36.61 MiB [----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------] 100.00% 9.89 MiB p/s 3.9s
2023-05-06T15:29:34.194Z        INFO    Vulnerability scanning is enabled
2023-05-06T15:29:34.194Z        INFO    Secret scanning is enabled
2023-05-06T15:29:34.194Z        INFO    If your scanning is slow, please try '--scanners vuln' to disable secret scanning
2023-05-06T15:29:34.194Z        INFO    Please see also https://aquasecurity.github.io/trivy/v0.41/docs/secret/scanning/#recommendation for faster secret detection
2023-05-06T15:29:39.449Z        INFO    Detected OS: alpine
2023-05-06T15:29:39.450Z        INFO    Detecting Alpine vulnerabilities...
2023-05-06T15:29:39.450Z        INFO    Number of language-specific files: 1
2023-05-06T15:29:39.450Z        INFO    Detecting python-pkg vulnerabilities...
2023-05-06T15:29:39.452Z        WARN    This OS version is no longer supported by the distribution: alpine 3.9.2
2023-05-06T15:29:39.452Z        WARN    The vulnerability detection may be insufficient because security updates are not provided

python:3.4-alpine (alpine 3.9.2)

Total: 37 (UNKNOWN: 0, LOW: 4, MEDIUM: 16, HIGH: 13, CRITICAL: 4)

┌──────────────┬────────────────┬──────────┬───────────────────┬───────────────┬──────────────────────────────────────────────────────────────┐
│   Library    │ Vulnerability  │ Severity │ Installed Version │ Fixed Version │                            Title                             │
├──────────────┼────────────────┼──────────┼───────────────────┼───────────────┼──────────────────────────────────────────────────────────────┤
│ expat        │ CVE-2018-20843 │ HIGH     │ 2.2.6-r0          │ 2.2.7-r0      │ expat: large number of colons in input makes parser consume  │
│              │                │          │                   │               │ high amount...                                               │
│              │                │          │                   │               │ https://avd.aquasec.com/nvd/cve-2018-20843                   │
│              ├────────────────┤          │                   ├───────────────┼──────────────────────────────────────────────────────────────┤
│              │ CVE-2019-15903 │          │                   │ 2.2.7-r1      │ expat: heap-based buffer over-read via crafted XML input     │
│              │                │          │                   │               │ https://avd.aquasec.com/nvd/cve-2019-15903                   │
├──────────────┼────────────────┼──────────┼───────────────────┼───────────────┼──────────────────────────────────────────────────────────────┤
│ libbz2       │ CVE-2019-12900 │ CRITICAL │ 1.0.6-r6          │ 1.0.6-r7      │ bzip2: out-of-bounds write in function BZ2_decompress        │
│              │                │          │                   │               │ https://avd.aquasec.com/nvd/cve-2019-12900                   │
├──────────────┼────────────────┼──────────┼───────────────────┼───────────────┼──────────────────────────────────────────────────────────────┤
│ libcrypto1.1 │ CVE-2019-1543  │ HIGH     │ 1.1.1a-r1         │ 1.1.1b-r1     │ openssl: ChaCha20-Poly1305 with long nonces                  │
│              │                │          │                   │               │ https://avd.aquasec.com/nvd/cve-2019-1543                    │
│              ├────────────────┤          │                   ├───────────────┼──────────────────────────────────────────────────────────────┤
│              │ CVE-2020-1967  │          │                   │ 1.1.1g-r0     │ openssl: Segmentation fault in SSL_check_chain causes denial │
│              │                │          │                   │               │ of service                                                   │
│              │                │          │                   │               │ https://avd.aquasec.com/nvd/cve-2020-1967                    │
│              ├────────────────┤          │                   ├───────────────┼──────────────────────────────────────────────────────────────┤
│              │ CVE-2021-23840 │          │                   │ 1.1.1j-r0     │ openssl: integer overflow in CipherUpdate                    │
│              │                │          │                   │               │ https://avd.aquasec.com/nvd/cve-2021-23840                   │
│              ├────────────────┤          │                   ├───────────────┼──────────────────────────────────────────────────────────────┤
│              │ CVE-2021-3450  │          │                   │ 1.1.1k-r0     │ openssl: CA certificate check bypass with                    │
│              │                │          │                   │               │ X509_V_FLAG_X509_STRICT                                      │
│              │                │          │                   │               │ https://avd.aquasec.com/nvd/cve-2021-3450                    │
│              ├────────────────┼──────────┤                   ├───────────────┼──────────────────────────────────────────────────────────────┤
│              │ CVE-2019-1547  │ MEDIUM   │                   │ 1.1.1d-r0     │ openssl: side-channel weak encryption vulnerability          │
│              │                │          │                   │               │ https://avd.aquasec.com/nvd/cve-2019-1547                    │
│              ├────────────────┤          │                   │               ├──────────────────────────────────────────────────────────────┤
│              │ CVE-2019-1549  │          │                   │               │ openssl: information disclosure in fork()                    │
│              │                │          │                   │               │ https://avd.aquasec.com/nvd/cve-2019-1549                    │
│              ├────────────────┤          │                   ├───────────────┼──────────────────────────────────────────────────────────────┤
│              │ CVE-2019-1551  │          │                   │ 1.1.1d-r2     │ openssl: Integer overflow in RSAZ modular exponentiation on  │
│              │                │          │                   │               │ x86_64                                                       │
│              │                │          │                   │               │ https://avd.aquasec.com/nvd/cve-2019-1551                    │
│              ├────────────────┤          │                   ├───────────────┼──────────────────────────────────────────────────────────────┤
│              │ CVE-2020-1971  │          │                   │ 1.1.1i-r0     │ openssl: EDIPARTYNAME NULL pointer de-reference              │
│              │                │          │                   │               │ https://avd.aquasec.com/nvd/cve-2020-1971                    │
│              ├────────────────┤          │                   ├───────────────┼──────────────────────────────────────────────────────────────┤
│              │ CVE-2021-23841 │          │                   │ 1.1.1j-r0     │ openssl: NULL pointer dereference in                         │
│              │                │          │                   │               │ X509_issuer_and_serial_hash()                                │
│              │                │          │                   │               │ https://avd.aquasec.com/nvd/cve-2021-23841                   │
│              ├────────────────┤          │                   ├───────────────┼──────────────────────────────────────────────────────────────┤
│              │ CVE-2021-3449  │          │                   │ 1.1.1k-r0     │ openssl: NULL pointer dereference in signature_algorithms    │
│              │                │          │                   │               │ processing                                                   │
│              │                │          │                   │               │ https://avd.aquasec.com/nvd/cve-2021-3449                    │
│              ├────────────────┼──────────┤                   ├───────────────┼──────────────────────────────────────────────────────────────┤
│              │ CVE-2019-1563  │ LOW      │                   │ 1.1.1d-r0     │ openssl: information disclosure in PKCS7_dataDecode and      │
│              │                │          │                   │               │ CMS_decrypt_set1_pkey                                        │
│              │                │          │                   │               │ https://avd.aquasec.com/nvd/cve-2019-1563                    │
│              ├────────────────┤          │                   ├───────────────┼──────────────────────────────────────────────────────────────┤
│              │ CVE-2021-23839 │          │                   │ 1.1.1j-r0     │ openssl: incorrect SSLv2 rollback protection                 │
│              │                │          │                   │               │ https://avd.aquasec.com/nvd/cve-2021-23839                   │
├──────────────┼────────────────┼──────────┤                   ├───────────────┼──────────────────────────────────────────────────────────────┤
│ libssl1.1    │ CVE-2019-1543  │ HIGH     │                   │ 1.1.1b-r1     │ openssl: ChaCha20-Poly1305 with long nonces                  │
│              │                │          │                   │               │ https://avd.aquasec.com/nvd/cve-2019-1543                    │
│              ├────────────────┤          │                   ├───────────────┼──────────────────────────────────────────────────────────────┤
│              │ CVE-2020-1967  │          │                   │ 1.1.1g-r0     │ openssl: Segmentation fault in SSL_check_chain causes denial │
│              │                │          │                   │               │ of service                                                   │
│              │                │          │                   │               │ https://avd.aquasec.com/nvd/cve-2020-1967                    │
│              ├────────────────┤          │                   ├───────────────┼──────────────────────────────────────────────────────────────┤
│              │ CVE-2021-23840 │          │                   │ 1.1.1j-r0     │ openssl: integer overflow in CipherUpdate                    │
│              │                │          │                   │               │ https://avd.aquasec.com/nvd/cve-2021-23840                   │
│              ├────────────────┤          │                   ├───────────────┼──────────────────────────────────────────────────────────────┤
│              │ CVE-2021-3450  │          │                   │ 1.1.1k-r0     │ openssl: CA certificate check bypass with                    │
│              │                │          │                   │               │ X509_V_FLAG_X509_STRICT                                      │
│              │                │          │                   │               │ https://avd.aquasec.com/nvd/cve-2021-3450                    │
│              ├────────────────┼──────────┤                   ├───────────────┼──────────────────────────────────────────────────────────────┤
│              │ CVE-2019-1547  │ MEDIUM   │                   │ 1.1.1d-r0     │ openssl: side-channel weak encryption vulnerability          │
│              │                │          │                   │               │ https://avd.aquasec.com/nvd/cve-2019-1547                    │
│              ├────────────────┤          │                   │               ├──────────────────────────────────────────────────────────────┤
│              │ CVE-2019-1549  │          │                   │               │ openssl: information disclosure in fork()                    │
│              │                │          │                   │               │ https://avd.aquasec.com/nvd/cve-2019-1549                    │
│              ├────────────────┤          │                   ├───────────────┼──────────────────────────────────────────────────────────────┤
│              │ CVE-2019-1551  │          │                   │ 1.1.1d-r2     │ openssl: Integer overflow in RSAZ modular exponentiation on  │
│              │                │          │                   │               │ x86_64                                                       │
│              │                │          │                   │               │ https://avd.aquasec.com/nvd/cve-2019-1551                    │
│              ├────────────────┤          │                   ├───────────────┼──────────────────────────────────────────────────────────────┤
│              │ CVE-2020-1971  │          │                   │ 1.1.1i-r0     │ openssl: EDIPARTYNAME NULL pointer de-reference              │
│              │                │          │                   │               │ https://avd.aquasec.com/nvd/cve-2020-1971                    │
│              ├────────────────┤          │                   ├───────────────┼──────────────────────────────────────────────────────────────┤
│              │ CVE-2021-23841 │          │                   │ 1.1.1j-r0     │ openssl: NULL pointer dereference in                         │
│              │                │          │                   │               │ X509_issuer_and_serial_hash()                                │
│              │                │          │                   │               │ https://avd.aquasec.com/nvd/cve-2021-23841                   │
│              ├────────────────┤          │                   ├───────────────┼──────────────────────────────────────────────────────────────┤
│              │ CVE-2021-3449  │          │                   │ 1.1.1k-r0     │ openssl: NULL pointer dereference in signature_algorithms    │
│              │                │          │                   │               │ processing                                                   │
│              │                │          │                   │               │ https://avd.aquasec.com/nvd/cve-2021-3449                    │
│              ├────────────────┼──────────┤                   ├───────────────┼──────────────────────────────────────────────────────────────┤
│              │ CVE-2019-1563  │ LOW      │                   │ 1.1.1d-r0     │ openssl: information disclosure in PKCS7_dataDecode and      │
│              │                │          │                   │               │ CMS_decrypt_set1_pkey                                        │
│              │                │          │                   │               │ https://avd.aquasec.com/nvd/cve-2019-1563                    │
│              ├────────────────┤          │                   ├───────────────┼──────────────────────────────────────────────────────────────┤
│              │ CVE-2021-23839 │          │                   │ 1.1.1j-r0     │ openssl: incorrect SSLv2 rollback protection                 │
│              │                │          │                   │               │ https://avd.aquasec.com/nvd/cve-2021-23839                   │
├──────────────┼────────────────┼──────────┼───────────────────┼───────────────┼──────────────────────────────────────────────────────────────┤
│ musl         │ CVE-2019-14697 │ CRITICAL │ 1.1.20-r4         │ 1.1.20-r5     │ musl libc through 1.1.23 has an x87 floating-point stack     │
│              │                │          │                   │               │ adjustment im ......                                         │
│              │                │          │                   │               │ https://avd.aquasec.com/nvd/cve-2019-14697                   │
│              ├────────────────┼──────────┤                   ├───────────────┼──────────────────────────────────────────────────────────────┤
│              │ CVE-2020-28928 │ MEDIUM   │                   │ 1.1.20-r6     │ In musl libc through 1.2.1, wcsnrtombs mishandles particular │
│              │                │          │                   │               │ combinati ...                                                │
│              │                │          │                   │               │ https://avd.aquasec.com/nvd/cve-2020-28928                   │
├──────────────┼────────────────┼──────────┤                   ├───────────────┼──────────────────────────────────────────────────────────────┤
│ musl-utils   │ CVE-2019-14697 │ CRITICAL │                   │ 1.1.20-r5     │ musl libc through 1.1.23 has an x87 floating-point stack     │
│              │                │          │                   │               │ adjustment im ......                                         │
│              │                │          │                   │               │ https://avd.aquasec.com/nvd/cve-2019-14697                   │
│              ├────────────────┼──────────┤                   ├───────────────┼──────────────────────────────────────────────────────────────┤
│              │ CVE-2020-28928 │ MEDIUM   │                   │ 1.1.20-r6     │ In musl libc through 1.2.1, wcsnrtombs mishandles particular │
│              │                │          │                   │               │ combinati ...                                                │
│              │                │          │                   │               │ https://avd.aquasec.com/nvd/cve-2020-28928                   │
├──────────────┼────────────────┼──────────┼───────────────────┼───────────────┼──────────────────────────────────────────────────────────────┤
│ sqlite-libs  │ CVE-2019-8457  │ CRITICAL │ 3.26.0-r3         │ 3.28.0-r0     │ sqlite: heap out-of-bound read in function rtreenode()       │
│              │                │          │                   │               │ https://avd.aquasec.com/nvd/cve-2019-8457                    │
│              ├────────────────┼──────────┤                   ├───────────────┼──────────────────────────────────────────────────────────────┤
│              │ CVE-2019-19244 │ HIGH     │                   │ 3.28.0-r2     │ sqlite: allows a crash if a sub-select uses both DISTINCT    │
│              │                │          │                   │               │ and window...                                                │
│              │                │          │                   │               │ https://avd.aquasec.com/nvd/cve-2019-19244                   │
│              ├────────────────┤          │                   ├───────────────┼──────────────────────────────────────────────────────────────┤
│              │ CVE-2019-5018  │          │                   │ 3.28.0-r0     │ sqlite: Use-after-free in window function leading to remote  │
│              │                │          │                   │               │ code execution                                               │
│              │                │          │                   │               │ https://avd.aquasec.com/nvd/cve-2019-5018                    │
│              ├────────────────┤          │                   ├───────────────┼──────────────────────────────────────────────────────────────┤
│              │ CVE-2020-11655 │          │                   │ 3.28.0-r3     │ sqlite: malformed window-function query leads to DoS         │
│              │                │          │                   │               │ https://avd.aquasec.com/nvd/cve-2020-11655                   │
│              ├────────────────┼──────────┤                   ├───────────────┼──────────────────────────────────────────────────────────────┤
│              │ CVE-2019-16168 │ MEDIUM   │                   │ 3.28.0-r1     │ sqlite: Division by zero in whereLoopAddBtreeIndex in        │
│              │                │          │                   │               │ sqlite3.c                                                    │
│              │                │          │                   │               │ https://avd.aquasec.com/nvd/cve-2019-16168                   │
│              ├────────────────┤          │                   ├───────────────┼──────────────────────────────────────────────────────────────┤
│              │ CVE-2019-19242 │          │                   │ 3.28.0-r2     │ sqlite: SQL injection in sqlite3ExprCodeTarget in expr.c     │
│              │                │          │                   │               │ https://avd.aquasec.com/nvd/cve-2019-19242                   │
└──────────────┴────────────────┴──────────┴───────────────────┴───────────────┴──────────────────────────────────────────────────────────────┘
2023-05-06T15:29:39.463Z        INFO    Table result includes only package filenames. Use '--format json' option to get the full path to the package file.

Python (python-pkg)

Total: 4 (UNKNOWN: 0, LOW: 0, MEDIUM: 2, HIGH: 2, CRITICAL: 0)

┌───────────────────────┬────────────────┬──────────┬───────────────────┬───────────────┬─────────────────────────────────────────────────────────────┐
│        Library        │ Vulnerability  │ Severity │ Installed Version │ Fixed Version │                            Title                            │
├───────────────────────┼────────────────┼──────────┼───────────────────┼───────────────┼─────────────────────────────────────────────────────────────┤
│ pip (METADATA)        │ CVE-2019-20916 │ HIGH     │ 19.0.3            │ 19.2          │ python-pip: directory traversal in _download_http_url()     │
│                       │                │          │                   │               │ function in src/pip/_internal/download.py                   │
│                       │                │          │                   │               │ https://avd.aquasec.com/nvd/cve-2019-20916                  │
│                       ├────────────────┼──────────┤                   ├───────────────┼─────────────────────────────────────────────────────────────┤
│                       │ CVE-2021-3572  │ MEDIUM   │                   │ 21.1          │ python-pip: Incorrect handling of unicode separators in git │
│                       │                │          │                   │               │ references                                                  │
│                       │                │          │                   │               │ https://avd.aquasec.com/nvd/cve-2021-3572                   │
├───────────────────────┼────────────────┤          ├───────────────────┼───────────────┼─────────────────────────────────────────────────────────────┤
│ setuptools (METADATA) │ CVE-2022-40897 │          │ 40.8.0            │ 65.5.1        │ Regular Expression Denial of Service (ReDoS) in             │
│                       │                │          │                   │               │ package_index.py                                            │
│                       │                │          │                   │               │ https://avd.aquasec.com/nvd/cve-2022-40897                  │
├───────────────────────┼────────────────┼──────────┼───────────────────┼───────────────┼─────────────────────────────────────────────────────────────┤
│ wheel (METADATA)      │ CVE-2022-40898 │ HIGH     │ 0.33.1            │ 0.38.1        │ remote attackers can cause denial of service via attacker   │
│                       │                │          │                   │               │ controlled input...                                         │
│                       │                │          │                   │               │ https://avd.aquasec.com/nvd/cve-2022-40898                  │
└───────────────────────┴────────────────┴──────────┴───────────────────┴───────────────┴─────────────────────────────────────────────────────────────┘
```
</details>

## Dockerfile scanning

### Using CLI

You can scan a Dockerfile by running the _Trivy_ scan on the Dockerfile, e.g., scanning-targets/Dockerfile.

```bash
trivy config scanning-targets/Dockerfile
```

### In Dockerfile

You can also scan a Dockerfile by embedding and running the _Trivy_ scan during the build, e.g., scanning-targets/Dockerfile.

```bash
docker build -t scanned-image scanning-targets/
```

The `--exit-code` specifies the exit code when any security issues are found, thus running it with the example from the Dockerfile in scanning-targets/ will fail the Dockerbuild if the status code is 1 (which in this case it is).
<details>
    <summary>The output:</summary>
[+] Building 16.2s (5/5) FINISHED
 => [internal] load build definition from Dockerfile                                                                0.0s
 => => transferring dockerfile: 262B                                                                                0.0s
 => [internal] load .dockerignore                                                                                   0.0s
 => => transferring context: 2B                                                                                     0.0s
 => [internal] load metadata for docker.io/library/alpine:3.7                                                       0.6s
 => CACHED [1/2] FROM docker.io/library/alpine:3.7@sha256:8421d9a84432575381bfabd248f1eb56f3aa21d9d7cd2511583c68c9  0.0s
 => ERROR [2/2] RUN apk add curl     && curl -sfL https://raw.githubusercontent.com/aquasecurity/trivy/master/con  15.5s
------
 > [2/2] RUN apk add curl     && curl -sfL https://raw.githubusercontent.com/aquasecurity/trivy/master/contrib/install.sh | sh -s -- -b /usr/local/bin     && trivy filesystem --exit-code 1 --no-progress /:
#5 0.366 fetch http://dl-cdn.alpinelinux.org/alpine/v3.7/main/x86_64/APKINDEX.tar.gz
#5 0.634 fetch http://dl-cdn.alpinelinux.org/alpine/v3.7/community/x86_64/APKINDEX.tar.gz
#5 0.778 (1/4) Installing ca-certificates (20190108-r0)
#5 0.852 (2/4) Installing libssh2 (1.9.0-r1)
#5 0.912 (3/4) Installing libcurl (7.61.1-r3)
#5 0.986 (4/4) Installing curl (7.61.1-r3)
#5 1.051 Executing busybox-1.27.2-r11.trigger
#5 1.056 Executing ca-certificates-20190108-r0.trigger
#5 1.119 OK: 6 MiB in 17 packages
#5 1.330 aquasecurity/trivy info checking GitHub for latest tag
#5 1.892 aquasecurity/trivy info found version: 0.41.0 for v0.41.0/Linux/64bit
#5 8.685 aquasecurity/trivy info installed /usr/local/bin/trivy
#5 9.131 2023-05-07T07:28:11.532Z       INFO    Need to update DB
#5 9.131 2023-05-07T07:28:11.532Z       INFO    DB Repository: ghcr.io/aquasecurity/trivy-db
#5 9.131 2023-05-07T07:28:11.532Z       INFO    Downloading DB...
#5 14.80 2023-05-07T07:28:17.195Z       INFO    Vulnerability scanning is enabled
#5 14.80 2023-05-07T07:28:17.196Z       INFO    Secret scanning is enabled
#5 14.80 2023-05-07T07:28:17.196Z       INFO    If your scanning is slow, please try '--scanners vuln' to disable secret scanning
#5 14.80 2023-05-07T07:28:17.196Z       INFO    Please see also https://aquasecurity.github.io/trivy/v0.41/docs/secret/scanning/#recommendation for faster secret detection
#5 14.99 2023-05-07T07:28:17.393Z       INFO    Detected OS: alpine
#5 14.99 2023-05-07T07:28:17.393Z       INFO    Detecting Alpine vulnerabilities...
#5 14.99 2023-05-07T07:28:17.394Z       INFO    Number of language-specific files: 0
#5 14.99 2023-05-07T07:28:17.394Z       WARN    This OS version is no longer supported by the distribution: alpine 3.7.3
#5 14.99 2023-05-07T07:28:17.394Z       WARN    The vulnerability detection may be insufficient because security updates are not provided
#5 15.00
#5 15.00 localhost (alpine 3.7.3)
#5 15.00 ========================
#5 15.00 Total: 2 (UNKNOWN: 0, LOW: 0, MEDIUM: 0, HIGH: 0, CRITICAL: 2)
#5 15.00
#5 15.00 ┌────────────┬────────────────┬──────────┬───────────────────┬───────────────┬──────────────────────────────────────────────────────────┐
#5 15.00 │  Library   │ Vulnerability  │ Severity │ Installed Version │ Fixed Version │                          Title                           │
#5 15.00 ├────────────┼────────────────┼──────────┼───────────────────┼───────────────┼──────────────────────────────────────────────────────────┤
#5 15.00 │ musl       │ CVE-2019-14697 │ CRITICAL │ 1.1.18-r3         │ 1.1.18-r4     │ musl libc through 1.1.23 has an x87 floating-point stack │
#5 15.00 │            │                │          │                   │               │ adjustment im ......
                        │
#5 15.00 │            │                │          │                   │               │ https://avd.aquasec.com/nvd/cve-2019-14697               │
#5 15.00 ├────────────┤                │          │                   │               │
                        │
#5 15.00 │ musl-utils │                │          │                   │               │
                        │
#5 15.00 │            │                │          │                   │               │
                        │
#5 15.00 │            │                │          │                   │               │
                        │
#5 15.00 └────────────┴────────────────┴──────────┴───────────────────┴───────────────┴──────────────────────────────────────────────────────────┘
------
executor failed running [/bin/sh -c apk add curl     && curl -sfL https://raw.githubusercontent.com/aquasecurity/trivy/master/contrib/install.sh | sh -s -- -b /usr/local/bin     && trivy filesystem --exit-code 1 --no-progress /]: exit code: 1
</details>

## GitHub (GH) Action scanning

The .github/workflows/trivy-scann.yaml show how to integrate Dockerfile scanning using Trivy and GH Action. You will find the results in the Security tab in GH.

## Setup Trivy in K8s

To create a cluster, run the following command:

```bash
kind create cluster --name trivy-demo
```

### Get the kubeconfig

```bash
kind get kubeconfig --name trivy-demo > ~/.kube/config
```

### Install Trivy using Helm

Following the instructions [here](https://aquasecurity.github.io/trivy-operator/v0.13.2/getting-started/installation/helm/) to install Trivy using Helm.

### Get report

```bash
