# mpvd (Mozilla Products Vulnerability Dataset)

### The following information is up-to-date as of August 17, 2023.
- The data will be updated periodically to account for new vulnerabilities provided in security advisories for updates to Mozilla products.

#### NOTE: The dataset is not 100% complete due to unavailable data or other issues encountered while scraping and parsing.

##### NOTE: Noisy data might be present in relation to the provided `vulnerable` and `fixed` source code files. This noisy data comes from files that might be considered irrelevant such as those with certain file extensions or keywords within the filename (e.g. `test`, `readme`, etc.). Although steps have been taken to mitigate these files in the overall dataset, they might still exist in some manner.

### Summary

This repository contains a dataset of source code files related to the known vulnerabilities in [Mozilla products](https://www.mozilla.org/en-US/security/known-vulnerabilities/). Advisories are available for the following products: [Firefox](https://www.mozilla.org/en-US/security/known-vulnerabilities/firefox/), [Firefox ESR](https://www.mozilla.org/en-US/security/known-vulnerabilities/firefox-esr/), [Firefox for iOS](https://www.mozilla.org/en-US/security/known-vulnerabilities/firefox-for-ios/), [Firefox OS](https://www.mozilla.org/en-US/security/known-vulnerabilities/firefox-os/), [Mozilla VPN](https://www.mozilla.org/en-US/security/known-vulnerabilities/mozilla-vpn/), [Thunderbird](https://www.mozilla.org/en-US/security/known-vulnerabilities/thunderbird/), [Thunderbird ESR](https://www.mozilla.org/en-US/security/known-vulnerabilities/thunderbird-esr/), and [SeaMonkey](https://www.mozilla.org/en-US/security/known-vulnerabilities/seamonkey/).

Additional vulnerability data related to the security advisories as well as the associated Bug IDs are also included.

### Cite
If you plan to use this data for your work, please provide a citation / reference.

Napier, K. Mozilla products vulnerability dataset [Data set]. https://github.com/krn65/mpvd

@misc{Napier_Mozilla_products_vulnerability,
author = {Napier, Kollin},
title = {{Mozilla products vulnerability dataset}},
url = {https://github.com/krn65/mpvd}
}

### Descriptions

The `product_data` folder contains a `.csv` file for each product that provides the following data from available security advisories: `version` (of product that fixed vulnerability), `CVE ID(s)`, `advisory` (ID from Mozilla), `title`, `reporter`, `impact` (defined by Mozilla), `description`, and `Bug ID(s)`. The product security advisory data is sorted in descending order starting with the most recent version.

The `product_bug_ids` folder contains a `.txt` file for each product that provides a list of Bug IDs found within the security advisories for each product. There is also a file titled `all_bug_ids-unique.txt` that provides a combined list of all the Bug IDs from all products which is sorted with duplicates removed.

Only source code files that have the following file extensions are scraped and part of the dataset: `.js`, `.java`, `.c`, `.cc`, `.cpp`, `.c++`, `.cp`, `.cxx`, `.h`, `.hh`, `.hpp`, `.py`

The `source_code-vulnerable.7z` file contains a folder of `"vulnerable"` (older) versions of source code files for all products before a vulnerability was fixed. The `source_code-fixed.7z` file contains a folder of `"fixed"` (newer) versions of source code files for all products after a vulnerability was fixed.

- **Note:** A scraped `"vulnerable"` source code file is not necessarily the original state of the file which created the vulnerability. It is just the last instance of the file where the vulnerability was still present (aka the parent revision which comes before the revision that fixed the vulnerability).

Each source code filename is labeled as `bug_id`-`revision_id`-`status`-`original_filename`.`extension`. The `bug_id` refers to the Bugzilla entry. The `revision_id` refers to the commit ([Phabricator](https://phabricator.services.mozilla.com/)) or revision ([Mercurial](https://hg.mozilla.org/)) ID for the files related to the Bugzilla entry of the Bug ID. The `status` refers to either `vulnerable` (old) or `fixed` (new) source code. The `original_filename` represents the name of the file that was changed. When writing the file, the filename was adjusted by replacing backslashes (`\`) with underscores (`_`). The `extension` refers to the file extension.

Both `.7z` files contain `8,400` source code files from all Mozilla products with a variety of file extensions. Only `2,638` of the total `3,466` unique Bug IDs are represented from the downloaded source code files. Only instances of source code files that have content (not empty) for both the `fixed` and `vulnerable` versions are included in the dataset. For example, if a source code file was created or deleted between a revision (current and parent), then that file is ignored. As stated earlier, this is due to unavailable data or other issues encountered while scraping or parsing the associated product security advisory data. Only Bugzilla entries that are public, have a status of `Closed`, and available attachments (table of revisions) are considered.
