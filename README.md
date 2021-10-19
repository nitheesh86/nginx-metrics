# nginx-metrics

docker container run --rm -d -v $(pwd)/nginx.conf:/etc/nginx/conf.d/default.conf -p 80:80 --name nginx nginx

docker container run -d --rm -p 9113:9113 --name nginx-exporter nginx/nginx-prometheus-exporter -nginx.scrape-uri http://172.17.0.2:80/metrics

# 172.17.0.2:80 you have to find the nginx container id

nginx inspect "nginx container id"

docker container run -d --rm -p 9090:9090 -v $(pwd)/prometheus.yml:/etc/prometheus/prometheus.yml --name prometheus prom/prometheus

Replace the promethus url in  - targets: ['172.17.0.3:9113'] with nginx-exporter ip
