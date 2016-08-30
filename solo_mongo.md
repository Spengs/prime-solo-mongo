<!-- Create a collection named orders. -->
db.createCollection('orders')
var orders = orders.db

<!-- Insert at least 3 documents that represent an order. IMPORTANT: See section below for fields. -->
orders.insert({orderDate: new Date('August 29, 2016'), orderTotal: 100.00, lineItems: [{unitPrice: 100, quantity: 1, productName: "Thing"}]})

orders.insert({orderDate: new Date('July 1, 1985'), orderTotal: 50, lineItems: [{unitPrice: 10, quantity: 5, productName: "Jambox"}]})

orders.insert({orderDate: new Date('January 16, 2016'), orderTotal: 350.00, lineItems: [{unitPrice: 1, quantity: 350, productName: "Dr.Pepper"}]})


<!-- Find a single order document, any order document. -->
orders.findOne()

<!-- Find all orders and make them look pretty. -->
orders.find().pretty


<!-- Find all orders with an orderDate that is prior to 1/1/2016. -->
orders.find({orderDate: {$lt: new Date('January 1, 2016')}})

<!-- Find all orders with an orderDate that is after 1/1/2016. -->
orders.find({orderDate: {$gt: new Date('January 1, 2016')}})

<!-- Find orders with lineItems that have a quantity that is less than 50, but greater than 5. HINT: Look at $and and dot notation. -->
orders.find({$and: [ {"lineItems.quantity": { $lt: 50 } }, {"lineItems.quantity": { $gt: 5 } } ])


<!-- Update one of your line items to 42.99. HINT: Look at dot notation -->
orders.update({"lineItems.unitPrice": 1}, {$set: {unitPrice: 42.99}})

<!-- Remove one of your orders. --> -->
orders.remove({"orderTotal": 350})
