# App Services
## LMA
- Stop service lma-prod-ea-app-01 -> Working -> <mark style="background: #FFB8EBA6;">Failed</mark>
- Stop service lma-prod-sea-app-01 -> Working -> <mark style="background: #FFB8EBA6;">Failed</mark>
- Stop both -> Error -> <mark style="background: #FFB86CA6;">Pending</mark>
# ActiveMQ
- Stop activeMQ on fleetprdeaamq1a -> Working -> <mark style="background: #BBFABBA6;">OK</mark>
- Stop activeMQ on fleetprdseaamq1a -> Working -> <mark style="background: #BBFABBA6;">OK</mark>
- Stop on both -> Error -> <mark style="background: #BBFABBA6;">OK</mark>

# DB
- Failover lma-prod-sea-sqlsrv-01 primary -> Working -> <mark style="background: #BBFABBA6;">OK</mark>
- Failover lma-prod-ea-sqlsrv-01 -> Working -> <mark style="background: #BBFABBA6;">OK</mark>