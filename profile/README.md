# IB-Ruby

Ruby Implementation of the Interactive Brokers Trader Workstation (TWS) API.

__Documentation: [https://ib-ruby.github.io/ib-doc/](https://ib-ruby.github.io/ib-doc/)__

A plain vanilla access is provided through [ib-api](https://github.com/ib-ruby/ib-api).  
**_ib-api_** sends Messages to the TWS-API and stores the response in a `received`-array.
The program just waits for the correct response

```ruby
the_stock =  IB::Stock.new symbol: 'GE'
limit_order = IB::Order.new  limit_price: 35, order_type: 'LMT',  total_quantity: 100, action: :buy
ib.send_message :PlaceOrder,
        :order => limit_order,
        :contract => the_stock,
        :local_id => ib.next_local_id

# wait until the orderstate message returned
ib.wait_for :OrderStatus
```

Alternatively, its possible to subscribe to certain messages

```ruby
ib.subscribe(:Alert, :ContractData, :ContractDataEnd ) do |msg| 
	case msg
	when Messages::Incoming::Alert
		  # do something asynchronous
	when Messages::Incoming::ContractDataEnd 
       # do something asyncronous
  else
      # asynchronous response to ContractData
  end  
 end
 # perform request
 request_id = ib.send_message :RequestContractData, :contract => Stock.new(symbol: 'T')
```

## IB-Gateway

To ease the access of the data on the tws-servers, [ib-extensions](https://github.com/ib-ruby/ib-extensions) provides helpers and macros 

* Verifiyng of contracts
* get Market-Price, Option-Greeks from a single contract
* load EOD-Data
* define Ordertypes, ie.  Limit.order, Stop.order ...
* easily define Straddles, Strangles, Calendars, Butterflies and other option-spreads




