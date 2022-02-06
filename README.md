# Kubernetes Config

This repo includes some of the configurations I use for running an API service & a MySQL DB on my development machine and learned after reading: [The Kubernetes Book](https://www.amazon.com/Kubernetes-Book-Nigel-Poulton/dp/1521823634)

---

## Contents

Brief description of each folder content

### API

- **api_deployment**: Creates new `ReplicaSet` for the api service
- **api_service**: Creates a ClusterIP service for the `Deployment` for other pods to be able to access it via IP if required
- **api_ingress**: Creates an ingress controller for mapping host names with the service exposing our deployment
- **api_pod**: Creates a new pod for the service

---

### Database

- **db_secret**: Contains credentials used by the database container
- **database_statefulset**: Creates a `StatefulSet` for the database in-order for its data to survive node failures/reboots ...etc
- **database_deployment**: Creates a `ReplicaSet` for the database. However; data do not survive node failures in replica set.
- **database_service**: Creates a NodePort service for the `Deployment` for other pods to be able to access it via IP if required. Although this isn't required was added for the sake of practicing
- **database_pod**: Creates new pod for the database

---

## Namespace

- **some_namespace**: Creates new namespace on the cluster

---

## PersistedVolume

- **persisted_volume_claim**: Creates a new claim to be used by pods so that they can access the required persisted volume
- **persisted_volume**: Creates a new persisted volume of type `LocalStorage`

---

## Security Policy

- **resourceQuota**: Creates a limit for number of pods that can be created
- **ro-filesystem**: Makes sure pod has readonly permissions on filesystem and are run as non root

---

## Stand alone files

- **ingress**: Another ingress controller file for praciticing

---

## License

```markdown
MIT License

Copyright (c) 2021

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```
