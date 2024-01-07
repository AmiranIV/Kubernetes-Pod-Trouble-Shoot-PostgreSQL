#### Generated a Secret:

kubectl create secret generic postgres-secret --from-literal=postgres-password=your-password-here


#### Command you provided is connecting to the PostgreSQL server specified by the -h (host), -U (username), and -c (SQL command) options.

kubectl run -i --tty --rm postgres-client --image=postgres:11.22-bullseye --restart=Never -- /bin/sh -c "PGPASSWORD=<your-password-here> psql -h postgres-service -U postgres -c '\list'"

#### Breakdown of the command:
kubectl run: This command is used to run a specified image in a pod.

-i --tty --rm: These options enable an interactive and pseudo-TTY session and remove the pod after it's terminated.

postgres-client: This is the name given to the pod.

--image=postgres:11.22-bullseye: Specifies the Docker image to use for the pod, which is PostgreSQL version 11.22 on Debian Bullseye in this case.

--restart=Never: Ensures that the pod does not automatically restart.

/bin/sh -c "PGPASSWORD= psql -h postgres-service -U postgres -c '\list'": This is the command that runs inside the pod. It sets the PGPASSWORD environment variable to the password "1234" and then uses psql to connect to the PostgreSQL server specified by -h (host) as postgres-service, with the username -U postgres, and executes the SQL command \list, which lists the available databases.


#### For info:

kubectl describe pod postgres-deployment-<id>

kubectl logs postgres-deployment-<id>

#### Log in to the Pod:

kubectl exec -it postgres-deployment-<id> /bin/bash
