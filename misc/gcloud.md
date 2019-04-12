<!-- TITLE: Gcloud -->
<!-- SUBTITLE: A quick summary of Gcloud -->

Error:

```text
"ServiceException: 401 Anonymous caller does not have storage.objects.create access to ....."
```
Solution:

```sh
gcloud auth  activate-service-account   --key-file=my.json
```
