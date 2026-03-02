# Validity Everest API - CSV Batch Domain Query Tool v2.0

A powerful and robust Python script designed to batch query domains against the Validity Everest API. 

Version 2.0 introduces a strict **subdomain filtering logic**, ensuring that only genuine subdomains (matching the exact top-level domain) are aggregated. This prevents skewed data from different domains (e.g., `example.jp` will no longer be incorrectly aggregated under `example.com`), providing highly accurate sending volume and ESP (Email Service Provider) competitor intelligence.

## ✨ Key Features

* **Smart CSV Parsing:** Automatically detects the domain column in your CSV files. Supports multiple text encodings (UTF-8, GBK, etc.) to prevent read errors.
* **Strict Subdomain Filtering (v2.0):** Isolates true subdomains from mixed API results, guaranteeing that volume and ESP data are highly relevant.
* **Comprehensive Insights:** Retrieves valid subdomains, filtered domains, estimated sending volume, and ESP usage percentages.
* **Resume Capability:** Automatically saves progress to a local `.progress_v2.json` file. If the script is interrupted or stopped, you can safely restart it without querying previously processed domains.
* **Rate Limiting & Auto-Retry:** Built-in sleep intervals and retry logic to gracefully handle API limits and temporary network errors.

## 🛠 Prerequisites

* Python 3.6 or higher
* A valid Validity Everest API Key

## 📦 Installation

1. Clone this repository or download the source code.
2. Install the required dependencies using `pip`:

```bash
pip install -r requirements.txt
(Note: The script also includes an auto-installer for dependencies if you run it directly without installing them first, but using requirements.txt is the recommended best practice.)

🚀 Usage
Run the script via your terminal or command prompt:

Bash
python everest_query_v2.py
Follow the interactive prompts:

Paste your Validity Everest API Key.

Provide the absolute or relative path to your Input CSV file.

Confirm the automatically detected domain column (or manually select it).

📊 Output Format
The script will generate a new CSV file named [original_filename]_result_v2.csv in the same directory. It preserves all your original columns and appends the following 5 core intelligence columns:

ESP(仅子域名) / ESP (Subdomains Only): The Email Service Providers used by the domain.

ESP占比 / ESP Percentage: The market share percentage of each ESP detected.

有效子域名 / Valid Subdomains: A semicolon-separated list of genuine subdomains verified by the v2.0 logic.

被过滤域名(不同顶级域) / Filtered Out Domains: Domains returned by the API that were rejected because they belong to a different TLD (e.g., example.co.uk vs example.com).

发信量估计(仅子域名) / Estimated Volume (Subdomains Only): The aggregated email sending volume for the valid subdomains.

⚠️ Disclaimer
This is a third-party tool and is not officially affiliated with or endorsed by Validity. Please ensure you comply with Validity Everest's API Terms of Service and rate limits when using this script.
