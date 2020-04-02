# Github Action for Google Cloud Run

A GitHub Action for building docker image and deploying revisions to Google Cloud Run.

## Usage

In your actions workflow, insert this:

```bash
- name: Build, Push and Deploy service to Google Cloud Run
  uses: ThomFree/action-build-cloud-run@1.1
  with:
    image: [your-hostname]/[your-project]/[image]
    service: [your-service]
    project: [your-project]
    region: [gcp-region]
    service key: ${{ secrets.GCLOUD_AUTH }}
```

Your `GCLOUD_AUTH` secret (or whatever you name it) must be a base64 encoded
gcloud service key with the following permissions:
- Service Account User
- Cloud Run Admin
- Storage Admin

The image must be "pushable" to one of Google's container registries, i.e. it
should be in the `gcr.io/[project]/[image]` or `eu.gcr.io/[project]/[image]`
format.
