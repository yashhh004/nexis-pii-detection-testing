# nexis-pii-detection-testing

A small test script for validating PII detection behavior on Nexis (Intelation's anonymization/compliance platform), calling their Text Anonymization API directly.

What it does

Sends a set of UK National Insurance Number test cases — both invalid-format numbers (used to confirm real format-validation rules first) and genuinely valid ones — to Nexis's /api/text/ endpoint, and checks whether each is correctly detected and masked.

Why

Beta-testing Nexis surfaced an apparent detection gap on a specific NI number. Before reporting it as a bug, this script verifies the test data itself is valid (following real UK NINO format rules: 2-letter prefix, 6 digits, 1-letter suffix, with specific excluded letters/prefixes) — the same lesson learned earlier when an "undetected" Tax File Number turned out to fail its own checksum validation, not a real detection bug.

Result

Once tested with genuinely valid NI numbers (AB123456C, EG789012B, HS222555D, WY444888A, PM666111C), all were correctly detected and masked via the API — confirming detection works correctly on valid input, and the earlier flagged case was invalid test data, not a system gap.

Built with
Python, requests
Nexis Text Anonymization API
To run it yourself
Get a Nexis API key (Basic plan or higher)
Replace the placeholder in the script with your own key
Run it — adjust the text field to test your own cases
