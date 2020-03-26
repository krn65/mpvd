# mpvd (Mozilla Products Vulnerability Data)

### The following information is accurate as of March 26, 2020.

#### NOTE: The data is not 100% complete due to issues encountered while scraping and parsing.


##### NOTE: Noisy data might be present in relation to the provided vulnerable source code files. This noisy data comes from files that might be considered irrelevant such as those with certain file extensions or keywords within the filename (e.g. `test`, `readme`, etc.). Although steps have been taken to mitigate these files in the overall data, they might still exist in some manner.

This repository contains data related to the known vulnerabilities in [Mozilla products](https://www.mozilla.org/en-US/security/known-vulnerabilities/). Advisories are available for the following products: [Firefox](https://www.mozilla.org/en-US/security/known-vulnerabilities/firefox/), [Firefox ESR](https://www.mozilla.org/en-US/security/known-vulnerabilities/firefox-esr/), [Firefox OS](https://www.mozilla.org/en-US/security/known-vulnerabilities/firefox-os/), [Thunderbird](https://www.mozilla.org/en-US/security/known-vulnerabilities/thunderbird/), [Thunderbird ESR](https://www.mozilla.org/en-US/security/known-vulnerabilities/thunderbird-esr/), and [SeaMonkey](https://www.mozilla.org/en-US/security/known-vulnerabilities/seamonkey/).

The `product_data` folder contains a `.csv` file for each product that provides the following data: version (of product that fixed vulnerability), CVE ID(s), advisory (ID from Mozilla), title, reporter, impact (defined by Mozilla), description, and Bug ID(s). The data is sorted in descending order starting with the most recent version. In order to properly sort, versions lower than 10 appending a `0` to the beginning (e.g. version 9 becomes 09).

The `product_bug_ids` folder contains a `.txt` file for each product that provides a list of Bug IDs found within the vulnerability data for each product. There is also a file titled `all_bug_ids.txt` that provides a combined list of all the Bug IDs from all products which is sorted with duplicates removed.

The `vulnerable_source_code.zip` file contains a folder of vulnerable (previous) versions of source code files for all products before a vulnerability was mitigated. Each filename is labeled as `bug_id`-`revision_id`-`old`-`original_filename`.`extension`. The original filename was adjusted by replacing the backslash (`\`) with an underscore (`_`) to be able to write to file. The folder contains `4,659` files with a variety of file extensions. Only `1894` of the total `7868` Bug IDs are represented from the downloaded vulnerable source code files. As stated earlier this is due to issues encountered while scraping or parsing the associated vulnerability data.
