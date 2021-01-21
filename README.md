# [Cloud Run](https://cloud.google.com/run) Demo

Followed this [CodeLab](https://codelabs.developers.google.com/codelabs/cloud-run-hello-python3#0)

## Build

### Set ENV Vars for Convenience

```bash
export PROJECT_ID=$(gcloud config get-value project)
export DOCKER_IMG="gcr.io/$PROJECT_ID/helloworld"
```

### Build Container via Cloud Build

```bash
gcloud builds submit --tag $DOCKER_IMG
```

### Deploy to Cloud Run

```bash
gcloud run deploy helloworld \
  --image $DOCKER_IMG \
  --platform managed \
  --region us-east1 \
  --allow-unauthenticated
```

### Get service URL

```bash
export SERVICE_URL=$( \
  gcloud run services describe helloworld \
  --platform managed \
  --region us-east1 \
  --format "value(status.url)" \
)
echo $SERVICE_URL
```

## Clean Up

### Delete Container Image

```bash
gcloud container images delete $DOCKER_IMG
```

#### Delete Cloud Run Service

```bash
gcloud run services delete helloworld \
--platform managed \
--region us-east1
```
