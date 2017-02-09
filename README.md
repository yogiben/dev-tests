# Dev tasks for position at Bitwala

## Tic-tac-toe (observed)
Build a simple tic-tac-toe game in your favourite JS flavour.

Should have ability to:
* Play the game
* Detect a victory
* Reset the game

## Lunch 12:30 !
We go eat.

## Simple API
Bitwala currently turns Bitcoin into Fiat (EUR, USD etc.).

Build a simple pricing REST API with the following endpoints.

```js
POST /invoice

{
  orders: [
    {
      currency: 'EUR',
      amount: 100.34
    },
    {
      currency: 'USD',
      amount: 60.00
    }
  ]
}

Response 200
{
  invoiceId: 123,
  payment: {
    currency: 'BTC',
    amount: 0.1
    fee: 0.01
    total: 0.11
  }
}
```
* POST an array of currency, amount pairs 
* Calculate the amount of BTC required to buy these
* Calculate our fee (see below)
* Store the result in a db (your choice) with an ID and return the result in the response


```js
GET /invoice/:id

Response 200

{
  invoiceId: 123,
  payment: {
    currency: 'BTC',
    amount: 0.1
    fee: 0.01
    total: 0.11
  }
}
```

#### Fee schedule (%age)
|        | EUR | USD | GBP |   |
|--------|-----|-----|-----|---|
| < 100  | 0.5 | 0.5 | 0.5 |   |
| >= 100 | 0.2 | 0.5 | 0.7 |   |
