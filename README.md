# Shop application Helm chart

This repository has the Helm chart for to applications 'products' and 'discounts'

![Shop Application](https://github.com/rhte2023-argo-rollouts/shop-application-helm-chart/raw/main/images/Shop.png)

It also has an umbrella Helm chart to deploy both applications together.
 
![Shop Umbrella Helm Chart](https://github.com/rhte2023-argo-rollouts/shop-application-helm-chart/raw/main/images/Shop-helm.png)
 
In the `Shop Umbrella Chart` we use several times the same charts as helm dependencies but with different names, if they are for Blue/Green or for Canary. This will allow us to have different configurations for each kind of deployment strategy.
 
This is the Chart.yaml
```
apiVersion: v2
name: shop-umbrella-blue-green
description: A Helm chart for Kubernetes
type: application
version: 0.1.0
appVersion: "1.16.0"
 
dependencies:
 - name: quarkus-helm-discounts
   version: 0.1.0
   alias: discounts-blue
   tags:
     - discounts-blue
 - name: quarkus-helm-discounts
   version: 0.1.0
   alias: discounts-green
   tags:
     - discounts-green
 - name: quarkus-base-networking
   version: 0.1.0
   alias: discountsNetworkingOnline 
   tags:
     - discountsNetworkingOnline
 - name: quarkus-base-networking
   version: 0.1.0
   alias: discountsNetworkingOffline
   tags:
     - discountsNetworkingOffline
 - name: quarkus-helm-products
   version: 0.1.0
   alias: products-blue
   tags:
     - products-blue
 - name: quarkus-helm-products
   version: 0.1.0
   alias: products-green
   tags:
     - products-green
 - name: quarkus-base-networking
   version: 0.1.0
   alias: productsNetworkingOnline
   tags:
     - productsNetworkingOnline
 - name: quarkus-base-networking
   version: 0.1.0
   alias: productsNetworkingOffline
   tags:
     - productsNetworkingOffline
```
 
We have packaged both applications in one chart, but we may have different charts per application.
