# pentaho-di-docker
A Docker image for Pentaho Data Integration (currently version 6.1)

## Starting the master

```javascript
{
  "id": "pentaho-di-master",
  "container": {
    "type": "DOCKER",
    "docker": {
      "image": "tobilg/pentaho-di:latest",
      "network": "HOST",
      "forcePullImage": true,
      "privileged": false
    }
  },
  "instances": 1,
  "cpus": 0.5,
  "mem": 2048
}
```

## Starting the slave

```javascript
{
  "id": "pentaho-di-slave",
  "container": {
    "type": "DOCKER",
    "docker": {
      "image": "tobilg/pentaho-di:latest",
      "network": "HOST",
      "forcePullImage": true,
      "privileged": false
    }
  },
  "instances": 1,
  "cpus": 0.5,
  "mem": 2048,
  "env": {
    "PDI_MASTER_SERVICE_NAME": "pentaho-di-master.marathon.mesos",
    "CARTE_INCLUDE_MASTERS": "Y",
    "CARTE_IS_MASTER": "N"
  }
}
```
