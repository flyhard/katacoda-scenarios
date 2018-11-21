## Create a chart

`helm create mytest`{{execute}}

## Search for your chart

`helm search mytest`{{execute}}

## push it to chartmuseum

`helm push mytest chartmuseum`{{execute}}

## Search for your chart (again)

### Update the repo locally
`helm repo update chartmuseum`{{execute}}
### search the repo
`helm search mytest`{{execute}}

## Deploy your chart

`helm upgrade --install test-chart chartmuseum/mytest`{{execute}}