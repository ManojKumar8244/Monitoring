# Project 5.1 Architecture

                    User
                      │
                      ▼
      Infrastructure Targets
     (Servers / Applications)
                      │
                      ▼
               Prometheus Server
            (Collects Metrics)
                      │
                      ▼
             Grafana Dashboard
             (Visualization)
                      │
                      ▼
          End User / Operations Team
          
# Project 5.2 Architecture

                    Application
                   / Server Logs
                        │
                        ▼
                   Filebeat Agent
                 (Collect Log Files)
                        │
                        ▼
                    Logstash
              (Parse & Transform)
                        │
                        ▼
                  Elasticsearch
                (Store & Index Logs)
                        │
                        ▼
                     Kibana
              (Search & Visualize)

              
# Project 5.3 Architecture


                        User
                          │
                          ▼
               Sample Spring Boot App
                          │
          ┌───────────────┴───────────────┐
          │                               │
          ▼                               ▼
  Prometheus Metrics              Jaeger Traces
          │                               │
          ▼                               │
     Prometheus ───────────────► Alertmanager
                                       │
                                       ▼
                           Email / Slack (Optional)

          Kibana is NOT required

          
# Project 5.4 Architecture


            Prometheus A      Prometheus B      Prometheus C
                 │                 │                 │
                 ▼                 ▼                 ▼
              Sidecar          Sidecar          Sidecar
                 │                 │                 │
                 └──────────┬──────┴──────┬──────────┘
                            ▼
                     Object Storage
                         (MinIO)
                            │
                            ▼
                      Thanos Query
                      (Global View)
                            │
                            ▼
                     Grafana Dashboard
