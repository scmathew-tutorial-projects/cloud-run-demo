# [Cloud Run](https://cloud.google.com/run) Demo

## Build

### Set Project ID ENV Var for Convenience

```bash
export GOOGLE_CLOUD_PROJECT=<PROJECT_ID>
```

### Build Container via Cloud Build

```bash
gcloud builds submit --tag gcr.io/${GOOGLE_CLOUD_PROJECT}/helloworld
```

### Deploy to Cloud Run

```bash
gcloud run deploy helloworld \
--image gcr.io/${GOOGLE_CLOUD_PROJECT}/helloworld
```
