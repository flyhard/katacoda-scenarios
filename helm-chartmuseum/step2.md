## Create a chart

`helm create mytest`{{execute}}

## Search for your chart

`helm search mytest`{{execute}}

## push it to chartmuseum

`helm push mychart chartmuseum`{{execute}}

## Search for your chart (again)

`helm search mytest`{{execute}}

## Deploy your chart

`helm upgrade --install test-chart chartmuseum/mytest`{{execute}}