# NOWPayments Go Library

[![NOWPayments API Docs](https://img.shields.io/badge/NOWPayments%20API%20Docs-blue?logo=postman&logoColor=white&labelColor=gray
)](https://documenter.getpostman.com/view/7907941/2s93JusNJt)
[![Go Reference](https://pkg.go.dev/badge/github.com/digilolnet/go-nowpayments.svg)](https://pkg.go.dev/github.com/digilolnet/go-nowpayments)
[![Go Report Card](https://goreportcard.com/badge/github.com/digilolnet/go-nowpayments)](https://goreportcard.com/report/github.com/digilolnet/go-nowpayments)

Topic|Endpoint|Package.Method|Implemented
---|:---|:---|:---:
Instant Payments Notifications|||Yes
||Verify signature|[ipn.VerifyRequestSignature(...)](https://pkg.go.dev/github.com/digilolnet/go-nowpayments/ipn#VerifyRequestSignature)|:heavy_check_mark:
Subscriptions|||Yes
||Create plan|[subscriptions.New(...)](https://pkg.go.dev/github.com/digilolnet/go-nowpayments/subscriptions#New)|:heavy_check_mark:
||Create an email subscription|[subscriptions.NewWithEmail(...)](https://pkg.go.dev/github.com/digilolnet/go-nowpayments/subscriptions#NewWithEmail)|:heavy_check_mark:
||Update plan|[subscriptions.Update(...)](https://pkg.go.dev/github.com/digilolnet/go-nowpayments/pkg/subscriptions#Update)|:heavy_check_mark:
||Get plan|[subscriptions.Get(...)](https://pkg.go.dev/github.com/digilolnet/go-nowpayments/subscriptions#Get)|:heavy_check_mark:
||List plans|[subscriptions.List(...)](https://pkg.go.dev/github.com/digilolnet/go-nowpayments/subscriptions#List)|:heavy_check_mark:
Recurring payments|||Yes
||Create|[recurring_payments.New(...)](https://pkg.go.dev/github.com/digilolnet/go-nowpayments/recurring_payments#New)|:heavy_check_mark:
||Get|[recurring_payments.Get(...)](https://pkg.go.dev/github.com/digilolnet/go-nowpayments/recurring_payments#Get)|:heavy_check_mark:
||Delete|[recurring_payments.Delete(...)](https://pkg.go.dev/github.com/digilolnet/go-nowpayments/recurring_payments#Delete)|:heavy_check_mark:
Billing (sub-partner API)|||Yes
||Deposit with payment|[custody.NewDepositWithPayment(...)](https://pkg.go.dev/github.com/digilolnet/go-nowpayments/custody#NewDepositWithPayment)|:heavy_check_mark:
||Deposit from master account|[custody.NewDepositFroMasterAccount(...)](https://pkg.go.dev/github.com/digilolnet/go-nowpayments/custody#NewDepositFroMasterAccount)|:heavy_check_mark:
||Get payments|[custody.GetPayments(...)](https://pkg.go.dev/github.com/digilolnet/go-nowpayments/custody#GetPayments)|:heavy_check_mark:
||Transfer between users|[custody.NewTransfer(...)](https://pkg.go.dev/github.com/digilolnet/go-nowpayments/pkg/custody#NewTransfer)|:heavy_check_mark:
||Get transfer|[custody.GetTransfer(...)](https://pkg.go.dev/github.com/digilolnet/go-nowpayments/custody#GetTransfer)|:heavy_check_mark:
||List transfers|[custody.ListTransfers(...)](https://pkg.go.dev/github.com/digilolnet/go-nowpayments/custody#ListTransfers)|:heavy_check_mark:
||Create user|[custody.NewUser(...)](https://pkg.go.dev/github.com/digilolnet/go-nowpayments/custody#NewUser)|:heavy_check_mark:
||List users|[custody.ListUsers(...)](https://pkg.go.dev/github.com/digilolnet/go-nowpayments/custody#NewUser)|:heavy_check_mark:
||Get user balance|[custody.GetBalance(...)](https://pkg.go.dev/github.com/digilolnet/go-nowpayments/custody#GetBalance)|:heavy_check_mark:
||Write-off to master account|[custody.NewWriteOffToMaster(...)](https://pkg.go.dev/github.com/digilolnet/go-nowpayments/custody#NewWriteOffToMaster)|:heavy_check_mark:
Payments|||Yes
||Get estimated price|[payments.EstimatedPrice(...)](https://pkg.go.dev/github.com/digilolnet/go-nowpayments/pkg/payments#EstimatedPrice)|:heavy_check_mark:
||Get the minimum payment amount|[payments.MinimumAmount(...)](https://pkg.go.dev/github.com/digilolnet/go-nowpayments/pkg/payments#MinimumAmount)|:heavy_check_mark:
||Get payment status|[payments.Status()](https://pkg.go.dev/github.com/digilolnet/go-nowpayments/pkg/payments#Status)|:heavy_check_mark:
||Get list of payments|[payments.List(...)](https://pkg.go.dev/github.com/digilolnet/go-nowpayments/pkg/payments#List)|:heavy_check_mark:
||Get/Update payment estimate|[payments.RefreshEstimatedPrice(...)](https://pkg.go.dev/github.com/digilolnet/go-nowpayments/pkg/payments#RefreshEstimatedPrice)|:heavy_check_mark:
||Create invoice|[payments.NewInvoice(...)](https://pkg.go.dev/github.com/digilolnet/go-nowpayments/pkg/payments#NewInvoice)|:heavy_check_mark:
||Create payment|[payments.New(...)](https://pkg.go.dev/github.com/digilolnet/go-nowpayments/pkg/payments#New)|:heavy_check_mark:
||Create payment from invoice|[payments.NewFromInvoice(...)](https://pkg.go.dev/github.com/digilolnet/go-nowpayments/pkg/payments#NewFromInvoice)|:heavy_check_mark:
Currencies|||Yes
||Get available currencies|[currencies.All()](https://pkg.go.dev/github.com/digilolnet/go-nowpayments/pkg/currencies#All)|:heavy_check_mark:
||Get available checked currencies|[currencies.Selected()](https://pkg.go.dev/github.com/digilolnet/go-nowpayments/pkg/currencies#Selected)|:heavy_check_mark:
Mass Payouts|||Partially
||List of payouts|[payouts.List(...)](https://pkg.go.dev/github.com/digilolnet/go-nowpayments/pkg/payouts#List)|:heavy_check_mark:
API status|||Yes
||Get API status|[core.Status()](https://pkg.go.dev/github.com/digilolnet/go-nowpayments/pkg/core#Status)|:heavy_check_mark:
Authentication|||Yes
||Authentication|[core.Authenticate(...)](https://pkg.go.dev/github.com/digilolnet/go-nowpayments/pkg/core#Authenticate)|:heavy_check_mark:

## Installation

```bash
go get github.com/digilolnet/go-nowpayments
```

## Usage

Just load the config with all the credentials from a file or using a `Reader` then display the NOWPayments' API status and the last 2 payments
made with:

```go
package main

import (
	"fmt"
	"log"
	"strings"

	"github.com/digilolnet/go-nowpayments/config"
	"github.com/digilolnet/go-nowpayments/core"
	"github.com/digilolnet/go-nowpayments/payments"
)

func main() {
	err := config.Load(strings.NewReader(`
            {
                  "server": "https://api-sandbox.nowpayments.io/v1",
                  "login": "some_email@domain.tld",
                  "password": "some_password",
                  "apiKey": "some_api_key"
            }
      `))

	if err != nil {
		log.Fatal(err)
	}

	core.UseBaseURL(core.BaseURL(config.Server()))
	core.UseClient(core.NewHTTPClient())

	ps, err := payments.List(&payments.ListOption{
		Limit: 2,
	})

	if err != nil {
		log.Fatal(err)
	}

	fmt.Printf("Last %d payments: %v\n", limit, ps)
}
```
