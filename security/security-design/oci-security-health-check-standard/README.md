# OCI Security Health Check - Standard Edition

Owner: Olaf Heimburger

Version: 230922

## Introduction
![Flyer](./files/resources/OCI_Security_Health_Check_Standard.png)

[Download the flyer](./files/resources/OCI%20Security%20Health%20Check%20-%20Standard%20-%20Flyer.pdf)

### When to use this asset?

The *OCI Security Health Check - Standard Edition* checks an OCI tenancy for [CIS Oracle Cloud Infrastructure Foundations Benchmark](https://www.cisecurity.org/benchmark/Oracle_Cloud) compliance.

### Complete Runtime Example

See the *OCI Security Health Check - Standard Edition* in action and watch the [OCI Health Checks - Self Service video](https://www.youtube.com/watch?v=EzjKLxfxaAM).

## Getting Started with the *OCI Security Health Check - Standard Edition*

### Download and verify the release file

Before running the *OCI Security Health Check - Standard Edition* you should download and verify it.

  - Download the latest distribution [oci-security-health-check-standard-230922.zip](https://github.com/oracle-devrel/technology-engineering/releases/download/oci-security-health-check-std-230922/oci-security-health-check-standard-230922.zip).
  - Download the respective checksum file:
    - [oci-security-health-check-standard-230922.sha512](https://github.com/oracle-devrel/technology-engineering/releases/download/oci-security-health-check-std-230922/oci-security-health-check-standard-230922.sha512).
    - [oci-security-health-check-standard-230922.sha512256](https://github.com/oracle-devrel/technology-engineering/releases/download/oci-security-health-check-std-230922/oci-security-health-check-standard-230922.sha512256).
  - Verify the integrity of the distribution. Both files must be in the same directory (for example, in your downloads directory).

    On MacOS:
    ```
    $ cd <your_downloads_directory>
    $ shasum -a 512256 -c oci-security-health-check-standard-230922.sha512256
    oci-security-health-check-standard-230922.zip: OK
    ```

    On Linux (including Cloud Shell):
    ```
    $ cd <your_downloads_directory>
    $ sha512sum -c oci-security-health-check-standard-230922.sha512
    oci-security-health-check-standard-230922.zip: OK
    ```

**Reject the downloaded file if the check fails!**

### Prepare the OCI Tenancy

#### Single Run

You can run the assessment as a member of the OCI `Administrator` group or
create a group for auditing and assign the respective user to it.

Running the assessment script as an OCI `Administrator` is the easiest and
quickest way. If you decide to use this option, please continue reading in
[Run the OCI Security Health Check in Cloud Shell](files/oci-security-health-check-standard/README.md#run-the-oci-security-health-check-in-cloud-shell).

#### Recurring usage

For recurring usage, setting up a group for auditing is recommended. For setting this up follow the steps documented next.

#### Setting up an *Auditor* group and policy

Using an auditor group is the recommended way to run the assessment script.
To create a group for auditing do the following steps:

  - Log into OCI Console as OCI administrator
  - Create a group `grp-auditors`
  - Create a policy `pcy-auditing` with these statements:
    ```
    allow group grp-auditors to inspect all-resources in tenancy
    allow group grp-auditors to read instances in tenancy
    allow group grp-auditors to read load-balancers in tenancy
    allow group grp-auditors to read buckets in tenancy
    allow group grp-auditors to read nat-gateways in tenancy
    allow group grp-auditors to read public-ips in tenancy
    allow group grp-auditors to read file-family in tenancy
    allow group grp-auditors to read instance-configurations in tenancy
    allow group grp-auditors to read network-security-groups in tenancy
    allow group grp-auditors to read resource-availability in tenancy
    allow group grp-auditors to read audit-events in tenancy
    allow group grp-auditors to read users in tenancy
    allow group grp-auditors to read vss-family in tenancy
    allow group grp-auditors to read dns in tenancy
    allow group grp-auditors to use cloud-shell in tenancy
    ```
  - Assign a user to the `grp-auditors` group
  - Log out of the OCI Console

## Credits

The *OCI Security Health Check - Standard Edition* streamlines the usage of the bundled [Compliance Checking Script](https://github.com/oracle-quickstart/oci-cis-landingzone-quickstart/blob/main/compliance-script.md) provided by the [CIS OCI Landing Zone Quick Start Template](https://github.com/oracle-quickstart/oci-cis-landingzone-quickstart).

The *OCI Security Health Check - Standard Edition* would not be possible without the great work of the [CIS OCI Landing Zone Quick Start Template Team](https://github.com/oracle-quickstart/oci-cis-landingzone-quickstart/graphs/contributors).

# License

Copyright (c) 2022-2023 Oracle and/or its affiliates.

Licensed under the Universal Permissive License (UPL), Version 1.0.

See [LICENSE](https://github.com/oracle-devrel/technology-engineering/blob/folder-structure/LICENSE) for more details.
