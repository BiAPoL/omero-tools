# How to transfer a dataset between two omero instances

It is a common task to transfer a dataset between two omero instances. This can be done using the OMERO API. The following steps will guide you through the process. Consider the following example: The dataset with id `dataset_id` is to be transferred from the source omero instance to the target omero instance.

Source omero instance: `172.26.122.141` (our test instance)
Target omore instance: `omero-int.biotec.tu-dresden.de`

## Preprequisites

Install the necessary packages - e.g., [omero-cli-transfer](https://github.com/ome/omero-cli-transfer) - on your local machine.

```bash
pip install omero-cli transfer
```

... that's it! Now you can start the transfer process.

## Transfer the data

To transfer the data, first log onto the source omero instance. This prompts you to enter your username and password.

```bash
omero login 172.26.122.141 --group <group_name>
```

Next, create a local copy of the specified dataset at a specified destination. The dataset will be named according to the path you provide.

```bash
omero transfer pack Dataset:<dataset_id> path/to/a/destination.tar
```	

Now, log onto the target omero instance.

```bash
omero login omero-int.biotec.tu-dresden.de --group <group_name>
```

Finally, upload the dataset to the target omero instance.

```bash
omero transfer unpack path/to/a/destination.tar
```

And that's it. 

*Note*: All of these steps can take some time, depending on the size of the dataset. Make sure to do this on a machine that has access to a high-speed internet connection.
*Note2*: During the upload, you will see the images being uploaded under arbitrary names. The correct names, annotations, etc. will be restored once the upload is complete.