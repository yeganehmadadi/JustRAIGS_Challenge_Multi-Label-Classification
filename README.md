# 🎁 JustRAIGS Challenge Pack 🎁

This Challenge Pack is a collection of JustRAIGS challenge codes and settings for IEEE ISBI 2024.

### ⚙️ Data uploading ⚙️
Challenges pull their data for running phases from archives.

For this challenge, two archives exist:

    justraigs-development-phase-data
    justraigs-test-phase-data

To upload data to archives, we've created an example script ./scripts/upload_to_justraigs-test-phase-data.py. This generates an archive_item_to_content_mapping.json that helps in setting up the evaluation method.

The script requires Python, SimpleITK, and gc-api to be installed. Read more about setting up gc-api in the [grand-challenge.org documentation](https://grand-challenge.org/documentation/what-can-gc-api-be-used-for/).
