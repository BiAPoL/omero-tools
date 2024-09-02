(OMERO.transfer_dataset)=
# How to transfer a dataset between two omero instances

It is a common task to transfer a dataset between two omero instances. This can be done using the OMERO API from the command line. The following steps will guide you through the process. Consider the following example: The dataset with id `dataset_id` is to be transferred from the source omero instance to the target omero instance.

Source omero instance: `source_hostname` (our test instance)
Target omero instance: `omero-int.biotec.tu-dresden.de`

## Preprequisites

Install the necessary packages - e.g., [omero-cli-transfer](https://github.com/ome/omero-cli-transfer) - on your local machine.

```bash
pip install omero-cli transfer
```

... that's it! Now you can start the transfer process.

## Transfer the data

To transfer the data, first log onto the source omero instance. This prompts you to enter your username and password. Of course, replace the `host_name` with the host name of your omero server.

```bash
omero login host_adress --group <group_name>
```

Next, create a local copy of the specified dataset at a specified destination. The dataset will be named according to the path you provide.

```bash
omero transfer pack Dataset:<dataset_id> path/to/a/destination.tar
```	

Now, log onto the target omero instance - in this case, this is `omero-int.biotec.tu-dresden.de`. Again, replace the `group_name` with the name of the group you want to upload the dataset to.

```bash
omero login omero-int.biotec.tu-dresden.de --group <group_name>
```

Finally, upload the dataset to the target omero instance.

```bash
omero transfer unpack path/to/a/destination.tar
```

And that's it. 

```{note}
All of these steps can take some time, depending on the size of the dataset. Make sure to do this on a machine that has access to a high-speed internet connection.
```

```{note}
During the upload, you will see the images being uploaded under arbitrary names. The correct names, annotations, etc. will be restored once the upload is complete.
```
