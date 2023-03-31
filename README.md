# Python codin challenge

Hi and welcome to the faire.ai’s engineering challenge that we hope you will 
enjoy to develop with your best skills and creativity. The following sections 
describe the problem you have to solve and what we expect from your solution.

Imagine you’re working for a fintech company that collects information from 
bank accounts of people. The company wants to implement a new function that
computes the average balance for a collection of accounts , and it 
provides you with the following datasets:

* a dataset containing all the transactions currently in possession for 
  some bank accounts. The avaliable fields are the id of the account 
  to which each transaction pertains (`account_id`), the moment at 
  which each transaction was made (`value_timestamp`), and the amount 
  of the transaction (`amount`).
* a dataset containing information about the bank accounts. The available
  fields here are the id of each account (`account_id`), the time at 
  which that account was created in the company systems (`creation_timestamp`),
  and the account balance value at `creation_timestamp`
* a dataset that specifies for each account at which date to compute the 
  average balance. The fields here are the id of the account to consider
  (`account_id`), and the time at which the result is required for each
  account (`reference_timestamp`).

Your task is to build the function that computes the average value of the 
balance for each account, where the average is performed over the 90 days
before the `reference_timestamp`, i.e.

```math
\mbox{average\_booked\_balance} = \frac{\sum_{\mbox{day} \in D} \mbox{balance}_\mbox{day}}{90}
```

where

```math
D = \mbox{days between (reference\_timestamp - 90days) and (reference\_timestamp)}
```

For example if we have

| account_id | reference_timestamp     |
|------------|-------------------------|
| ac_1       | 2017-03-31 23:59:59.999 |
| ac_2       | 2017-04-15 23:59:59.999 |

the function should return:
* the average value of the balance for account `ac_1` over the daily balances 
  in the date range `2016-12-31 23:59:59.999` to `2016-03-31 23:59:59.999`
* the average value of the balance for account `ac_2` over the daily balances 
  in the date range `2017-01-15 23:59:59.999` to `2016-04-15 23:59:59.999`
