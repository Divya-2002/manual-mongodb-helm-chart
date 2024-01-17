Mongodb-helmchart

1. Accessing MongoDB:

   To access the MongoDB service from within the Kubernetes cluster:

   a. Use the following command to connect to the MongoDB shell:

      ```bash
      kubectl exec -it {{ include "mongodb-chart.fullname" . }} -- mongo -u admin -p password --authenticationDatabase admin
      ```

      Replace 'admin' with the desired database and 'password' with the actual password set in the values.yaml file.

   b. Alternatively, to connect from outside the cluster:

      - Ensure kubectl is installed and configured.
      - Use port forwarding to access the MongoDB service:

        ```bash
        kubectl port-forward svc/{{ include "mongodb-chart.fullname" . }} 27017:27017 --namespace {{ .Release.Namespace }}
        ```

      - Connect using a MongoDB client to 'localhost:27017' with the provided credentials.

2. Information:

   - MongoDB root username: admin
   - MongoDB root password: password
