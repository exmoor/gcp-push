# Github Action for GCP docker registry push

A GitHub Action for building docker image and deploying revisions to Google Cloud Run.

## Usage

In your actions workflow, insert this:

```bash
- name: Build, Push and Deploy service to Google Cloud Run
  uses: ThomFree/action-build-cloud-run@1.1
  with:
    image: [your-hostname]/[your-project]/[image]
    project: [your-project]
    region: [gcp-region]
    service key: ${{ secrets.GCLOUD_AUTH }}
```

Your `GCLOUD_AUTH` secret (or whatever you name it) must be a base64 encoded
gcloud service key.

The image must be "pushable" to one of Google's container registries, i.e. it
should be in the `gcr.io/[project]/[image]` or `eu.gcr.io/[project]/[image]`
format.
