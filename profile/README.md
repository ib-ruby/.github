# IB-Ruby

Ruby Implementation of the Interactive Brokers Trader Workstation (TWS) API.

__Documentation: [https://ib-ruby.github.io/ib-api/](https://ib-ruby.github.io/ib-api/)__

The TWS-API supports a variety of applications. It can be used to aggregate news, fetch quotes, download historical data, load option-chains and last not least to place orders.

**_ib-api_** provides a low-level interface to the Interactive Brokers TWS- or Gateway-API. 
Basically the user sends messages to the tws and subscribes to expected responses. 

**Plugins** extent its functionality and provide useful automations.

To experiment with the program, an [interactive console](https://ib-ruby.github.io/ib-api/console.html) is included

```
work:~/labor/ib-api/bin$ ./console 

>> IB-API Interactive Console <<
---------------------------------------------
Namespace is IB ! 
---------------------------------------------
W: Workflow::  -> gateway_mode
F: Connected to server, version: 165, using client-id: 2000,
   connection time: 2024-11-23 19:38:01 +0100 local, 2024-11-23T18:38:01+00:00 remote.
W: Workflow:: gateway_mode -> ready
A: Market data farm connection is OK:eufarm
A: HMDS data farm connection is inactive but should be available upon demand.euhmds
A: Sec-def data farm connection is OK:secdefeu
W: Workflow:: ready -> account_based_operations
W: Workflow:: account_based_operations -> account_based_orderflow
account_based_orderflow
I: DUXXXXXXX => Count of AccountValues: 134
I: DUYYYYYYY => Count of AccountValues: 135
A: API client has been unsubscribed from account data.
Connection established on  localhost:4002

┌────────────────────────────────────────────────────────────────────────┐
│                             Active Plugins                             │
├───────────────────┬──────────────────┬──────────────────┬──────────────┤
│ advanced-account  │ connection-tools │ managed-accounts │ market-price │
│ order-flow        │ order-prototypes │ process-orders   │ roll         │
│ spread-prototypes │ symbols          │ verify           │              |
└───────────────────┴──────────────────┴─────────────────────────────────┘

----> C    points to the connection-instance
---------------------------------------------
3.2.0 :001 > client =  C.clients.last
 => <demo_user DU4035279> 
3.2.0 :002 > puts client.portfolio_values.as_table
┌────────────┬───────────────────────┬───────┬────────┬────────┬──────────┬────────────┬──────────┐
│            │                       │ pos   │ entry  │ market │ value    │ unrealized │ realized │
╞════════════╪═══════════════════════╪═══════╪════════╪════════╪══════════╪════════════╪══════════╡
│ DU4035279  │ Stock: DBK EUR IBIS   │  1400 │ 10.511 │ 15.574 │  21803.6 │     7088.2 │          │
│ DU4035279  │ Stock: F USD NYSE     │  1300 │ 14.212 │  11.18 │  14534.0 │   -3941.47 │          │
│ DU4035279  │ Stock: LNZ EUR VSE    │   114 │ 45.949 │  29.55 │   3368.7 │   -1869.47 │          │
│ DU4035279  │ Stock: SIE EUR IBIS   │  -100 │ 179.91 │ 177.62 │ -17762.0 │      229.0 │          │
│ DU4035279  │ Stock: TKA EUR IBIS   │  1300 │  8.871 │  3.803 │   4943.9 │    -6588.4 │          │
│ DU4035279  │ Stock: TLT USD NASDAQ │ -1000 │ 90.772 │  90.45 │ -90450.0 │     322.23 │          │
│ DU4035279  │ Stock: TUI1 EUR IBIS  │   180 │  43.21 │  7.434 │  1338.12 │   -6439.68 │          │
└────────────┴───────────────────────┴───────┴────────┴────────┴──────────┴────────────┴──────────┘

```

