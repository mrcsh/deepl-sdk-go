deepl-sdk
===

This is an unofficial Go SDK for using the DeepL API.

# Usage

```bash
go get github.com/mrcsh/deepl-sdk
```

# Sample

```go
package main

import (
	"context"
	"fmt"
	"os"

	"github.com/michimani/deepl-sdk"
	"github.com/michimani/deepl-sdk/params"
	"github.com/michimani/deepl-sdk/types"
)

func main() {
	client, err := deepl.NewClient()
	if err != nil {
		fmt.Println(err)
		return
	}

	text := []string{
		"Привіт",
		"Це приклад тексту",
	}
	params := &params.TranslateTextParams{
		TargetLang: types.TargetLangEN,
		Text:       text,
	}

	res, errRes, err := c.TranslateText(context.TODO(), params)

	if err != nil {
		fmt.Println(err)
	}

	if errRes != nil {
		fmt.Println("ErrorResponse", errRes.Message)
	}

	for i := range res.Translations {
		fmt.Printf("%s -> %s\n", text[i], res.Translations[i].Text)
	}
}
```
