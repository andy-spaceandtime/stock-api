# Simple Stocks API made with Node.js

Node.js API to get updated stocks data.
Limited to 5 requests per minute.
Working with the Alphavantage API free version.

# Very limited functionality for now

If you get CORS issues, just plug in https://cors-anywhere.herokuapp.com/ before the fetch url

const request = await fetch('https://cors-anywhere.herokuapp.com/https://stocksapi.herokuapp.com/stock' ...  // code below

Sample single stock request with Javascript fetch:
```
const getStock = async ticker =>{
  console.log("Getting data");
  const request = await fetch('https://stocksapi.herokuapp.com/stock',{
    method: 'POST',
    headers: {
      'Content-Type': 'application/json'
    },

    body: JSON.stringify({
      'ticker': ticker,
      'type': 'daily'
    })
  })

  const data = await request.json()
  console.log(data);
  return data;
}

getStock('AAPL');
```

Sample multiple stocks request (with cors-anywhere to avoid CORS issues):

```
const getStocks = async tickersArray=>{
  console.log("Getting data");
  const request = await fetch('https://cors-anywhere.herokuapp.com/https://stocksapi.herokuapp.com/stocks',{
    method: 'POST', 
    headers: {
      'Content-Type': 'application/json'
      // 'Content-Type': 'application/x-www-form-urlencoded',
    },
    body: JSON.stringify({
      'tickers': tickersArray,
      'type': 'monthly'
    })
  })

  const data = await request.json()
  console.log(data);
  return data;
}

getStocks(['AAPL', 'MSFT', 'DIA']);
```

# body params
types: 
'monthly' 
'daily'

ticker: 'any-ticker' //example 'AAPL'
tickers: ['multiple', 'tickers', 'array']



# stock-api
