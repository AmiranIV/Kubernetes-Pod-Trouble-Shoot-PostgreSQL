Generated a Secret:

kubectl create secret generic postgres-secret --from-literal=postgres-password=your-password-here


Command you provided is connecting to the PostgreSQL server specified by the -h (host), -U (username), and -c (SQL command) options.

kubectl run -i --tty --rm postgres-client --image=postgres:11.22-bullseye --restart=Never -- /bin/sh -c "PGPASSWORD=<your-password-here> psql -h postgres-service -U postgres -c '\list'"
