

# Get kibana pod
 kubectl get pods -n kube-logging -o wide --show-labels --watch



# Forward to kibana

kubectl -n kube-logging port-forward $(kubectl -n kube-logging get pod -l app=kibana -o jsonpath='{.items[0].metadata.name}') 5601:5601


export NODE_PORT=$(kubectl -n kube-logging get -o jsonpath="{.spec.ports[0].nodePort}" services kibana)
export NODE_IP=$(kubectl -n kube-logging get nodes -o jsonpath="{.items[0].status.addresses[0].address}")
echo http://$NODE_IP:$NODE_PORT/


# Install heartbeat

helm install --name heartbeat heartbeat/values.yaml stable/heartbeat --namespace kube-logging

{
"name":"John",
"age":30,
"cars":[ "Ford", "BMW", "Fiat" ]
}

curl -XPOST http://localhost:5044 -H "Content-Type: application/json" -d @cars.json

curl -v http://10.105.61.176:5044 -H "Content-Type: application/json" -d "Hi"

