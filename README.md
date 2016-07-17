# mailchimp-go

mailchimp-go is a Go client for the MailChimp API v3.

While coverage of the MailChimp API is limited in the current state, the goal is to provide a basic structure that can be built upon to eventually have full coverage.

Contributing code to complete missing resources is greatly appreciated.

## Features

## Installation

Fetch the package from GitHub:

```sh
go get github.com/beeker1121/mailchimp-go
```

Import to your project:

```go
import mailchimp "github.com/beeker1121/mailchimp-go"
```

## Usage

At the moment, this library has minimal coverage of the MailChimp API.

### Add member to list

```go
package main

import (
	"fmt"

	mailchimp "github.com/beeker1121/mailchimp-go"
	"github.com/beeker1121/mailchimp-go/lists/members"
)

func main() {
	// Set API key.
	if err := mailchimp.SetKey("YOUR-API-KEY"); err != nil {
		fmt.Println(err)
		return
	}

	// Set request parameters.
	params := &members.NewParams{
		EmailAddress: "user@example.com",
		Status:       members.StatusSubscribed,
	}

	// Add the member to list 123456.
	member, err := members.New("123456", params)
	if err != nil {
		fmt.Println(err)
		return
	}

	fmt.Printf("%v\n", member)
}
```

## Benchmarks