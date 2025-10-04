**Vulnerability:** Found the endpoint that serves usage data to be scraped by a popular monitoring system (Prometheus) !!!

## What I did:
1. Clicked on the link to Prometheus Github
2. Looked for the endpoint which is /metrics
3. So I changed the URL to localhost:3000/metrics 

## Why happened:
I was able to access the metrics used by Promotheus on Juice Shop.

This exposes the website's sensitive data on backend processes such as the total balance of all users' digital wallets etc. that can be used by the attacker for recon 

## How to Fix:
- They should hide this. they probably forgot to hide it idk
