# 🎁 JustRAIGS Challenge Pack 🎁

This Challenge Pack is a collection of JustRAIGS challenge codes and settings for IEEE ISBI 2024.

If you have any questions, feel free to reach out to me at yeganeh.madadi@gmail.com.


### ⚙️ Data uploading ⚙️
Challenges pull their data for running phases from archives.

For this challenge, two archives exist:

    justraigs-development-phase-data
    justraigs-test-phase-data

To upload data to archives, we've created an example script ./scripts/upload_to_justraigs-test-phase-data.py. This generates an archive_item_to_content_mapping.json that helps in setting up the evaluation method.

The script requires Python, SimpleITK, and gc-api to be installed. Read more about setting up gc-api in the [grand-challenge.org documentation](https://grand-challenge.org/documentation/what-can-gc-api-be-used-for/).


### ⚙️ Example algorithm ⚙️

An example algorithm container is provided via: ./example-algorithm.

You can study it and run it by calling:

    $ cd ./example-algorithm
    $ docker build --tag example-algorithm . && \
        rm -f test/output/* && \
        docker run --rm --gpus all \
        --volume $(pwd)/test/input:/input \
        --volume $(pwd)/test/output:/output \
        example-algorithm

This should output something along the lines of:

    =+==+==+==+==+==+==+==+==+==+=
    Torch CUDA is available: True
            number of devices: 1
            current device: 0
            properties: _CudaDeviceProperties(name='NVIDIA GeForce GTX 1650 Ti', major=7, minor=5, total_memory=4095MB, multi_processor_count=16)
    =+==+==+==+==+==+==+==+==+==+=
    Input Files:
    [PosixPath('/input/2332ec76-d9ba-437f-b03b-1fbebaf99401.mha')]
    De-Stacked /tmp/tmp0drsxkpw/image_1.png
    De-Stacked /tmp/tmp0drsxkpw/image_2.png
    De-Stacked /tmp/tmp0drsxkpw/image_3.png

You can prep it for upload using:

    $  docker save example-algorithm | gzip -c > example-algorithm.tar.gz


### ⚙️ Example evaluation method ⚙️

An example evaluation method container is provided via: ./example-evaulation. It does not, currently, do any sensible evaluation.

You can study it and run it by calling:

    $ cd ./example-evaluation
    $ docker build --tag example-evaluation . && \
        rm -f test/output/* && \
        docker run --rm \
        --volume $(pwd)/test/input:/input \
        --volume $(pwd)/test/output:/output \
        example-evaluation

You can prep it for upload using:

    $  docker save example-evaluation | gzip -c > example-evaluation.tar.gz
