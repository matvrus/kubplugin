#!/bin/bash

# Define command-line arguments
NAMESPACE="$1"
COMMAND="$2"
RESOURCE_TYPE="$3"

# Retrieve resource usage statistics from Kubernetes
kubectl $COMMAND $RESOURCE_TYPE -n $NAMESPACE | tail -n +2 | while read -r line
do
  # Extract CPU and memory usage from the output
  NAME=$(echo "$line" | awk '{print $1}')
  CPU=$(echo "$line" | awk '{print $2}')
  MEMORY=$(echo "$line" | awk '{print $3}')

  # Output the statistics to the console with colors
echo -e "Resource: \e[1;36m$RESOURCE_TYPE\e[0m, Namespace: \e[1;33m$NAMESPACE\e[0m, Name: \e[1;35m$NAME\e[0m, CPU: \e[1;32m$CPU\e[0m, Memory: \e[1;34m$MEMORY\e[0m"
done

#   # Output the statistics to the console
#   echo "Resource: $RESOURCE_TYPE, Namespace: $NAMESPACE, Name: $NAME, CPU: $CPU, Memory: $MEMORY"
# done