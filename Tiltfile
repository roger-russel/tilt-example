load('ext://helm_resource', 'helm_resource', 'helm_repo')

# Install nginx-ingress
k8s_yaml(helm('charts/nginx-ingress', name="nginx-ingress"))

# Install prometheus
# helm_repo('prometheus-community', 'https://prometheus-community.github.io/helm-charts')
# helm_resource('local-prometheus', 'prometheus-community/prometheus', flags=['--version=24.3.0'])

# Install Grafana
# helm_repo('grafana', 'https://grafana.github.io/helm-charts')
# helm_resource('local-grafana', 'grafana/grafana', flags=['--version=6.59.4'])

# Install app
k8s_yaml(helm('charts/go-foo', name="go-foo"))

# Build: tell Tilt what images to build from which directories
docker_build('example/go-foo', './example/go-foo')

# Watch: tell Tilt how to connect locally (optional)
# k8s_resource('frontend', port_forwards=9999)
# k8s_resource('backend-api-1', port_forwards=3000)
# k8s_resource('local-grafana', port_forwards=8080)
# k8s_resource('local-prometheus', port_forwards=["9292:80"])
