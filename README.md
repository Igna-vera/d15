Resolución

```console


─>$ pm2 start ./src/server.js --name="ClusterEn8082" --watch -i 2  -- -p 8082


─>$ pm2 start ./src/server.js --name="ClusterEn8083" --watch -i 2  -- -p 8083


>$ pm2 start ./src/server.js --name="ClusterEn8084" --watch -i 2  -- -p 8084


─>$ pm2 start ./src/server.js --name="ClusterEn8085" --watch -i 2  -- -p 8085

```

Comprobamos la lista:

````console
╰─>pm2 list
┌┌─────┬──────────────────┬─────────────┬─────────┬─────────┬──────────┬────────┬──────┬───────────┬──────────┬──────────┬──────────┬──────────┐
│ id  │ name             │ namespace   │ version │ mode    │ pid      │ uptime │ ↺    │ status    │ cpu      │ mem      │ user     │ watching │
├─────┼──────────────────┼─────────────┼─────────┼─────────┼──────────┼────────┼──────┼───────────┼──────────┼──────────┼──────────┼──────────┤
│ 0   │ ClusterEn8082    │ default     │ 1.0.0   │ fork    │ 23116    │ 3m     │ 0    │ online    │ 0%       │ 26.6mb   │ ignac    │ disabled │
│ 7   │ ClusterEn8082    │ default     │ 1.0.0   │ fork    │ 18240    │ 3m     │ 0    │ online    │ 0%       │ 27.0mb   │ ignac    │ disabled │
│ 8   │ ClusterEn8082    │ default     │ 1.0.0   │ fork    │ 17120    │ 3m     │ 0    │ online    │ 0%       │ 27.1mb   │ ignac    │ disabled │
│ 1   │ ClusterEn8083    │ default     │ 1.0.0   │ cluster │ 23248    │ 3m     │ 0    │ online    │ 0%       │ 27.9mb   │ ignac    │ enabled  │
│ 2   │ ClusterEn8083    │ default     │ 1.0.0   │ cluster │ 21088    │ 3m     │ 0    │ online    │ 0%       │ 26.8mb   │ ignac    │ enabled  │
│ 3   │ ClusterEn8084    │ default     │ 1.0.0   │ cluster │ 20140    │ 3m     │ 0    │ online    │ 0%       │ 27.0mb   │ ignac    │ enabled  │
│ 4   │ ClusterEn8084    │ default     │ 1.0.0   │ cluster │ 27444    │ 3m     │ 0    │ online    │ 0%       │ 27.4mb   │ ignac    │ enabled  │
│ 5   │ ClusterEn8085    │ default     │ 1.0.0   │ cluster │ 25832    │ 3m     │ 0    │ online    │ 0%       │ 28.3mb   │ ignac    │ enabled  │
│ 6   │ ClusterEn8085    │ default     │ 1.0.0   │ cluster │ 28340    │ 3m     │ 0    │ online    │ 0%       │ 28.5mb   │ ignac    │ enabled  │
└─────┴──────────────────┴─────────────┴─────────┴─────────┴──────────┴────────┴──────┴───────────┴──────────┴──────────┴──────────┴──────────┘




Agregamos un log cuando se genere la lista y podemos comprobarlo a través de **pm2 monit**

```console


─>$ pm2 monit


─ Process List ───────────────────┐┌──  ClusterEn8082 Logs  ──────────────────────────────────────────────────────────┐│[ 0] ClusterEn8082      Mem:  27  ││                                                                                  ││[ 7] ClusterEn8082      Mem:  27  ││                                                                                  ││[ 8] ClusterEn8082      Mem:  27  ││                                                                                  ││[ 1] ClusterEn8083      Mem:  28  ││                                                                                  ││[ 2] ClusterEn8083      Mem:  27  ││                                                                                  ││[ 3] ClusterEn8084      Mem:  27  ││                                                                                  ││[ 4] ClusterEn8084      Mem:  27  ││                                                                                  ││[ 5] ClusterEn8085      Mem:  27  ││                                                                                  ││[ 6] ClusterEn8085      Mem:  28  ││                                                                                  ││                                  ││                                                                                  ││                                  ││                                                                                  ││                                  ││                                                                                  ││                                  ││                                                                                  ││                                  ││                                                                                  ││                                  ││                                                                                  ││                                  ││                                                                                  ││                                  ││                                                                                  ││                                  ││                                                                                  ││                                  ││                                                                                  │└──────────────────────────────────┘└──────────────────────────────────────────────────────────────────────────────────┘┌─ Custom Metrics ─────────────────┐┌─ Metadata ───────────────────────────────────────────────────────────────────────┐│ Used Heap Size         5.09 MiB  ││ App Name              ClusterEn8082                                              ││ Heap Usage              74.55 %  ││ Namespace             default                                                    ││ Heap Size              6.82 MiB  ││ Version               1.0.0                                                      ││ Event Loop Latency p95           ││ Restarts              0                                                          ││ Event Loop Latency      8.51 ms  ││ Uptime                26m
````
