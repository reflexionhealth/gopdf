 gopdf
=======

gopdf is a simple library for generating PDF document written in Go lang.


### Notice

Forked from signintech/gopdf to support loading a font from in-memory.


 Installation
--------------
 ```
 go get -u github.com/reflexionhealth/gopdf
 ```


 Sample code
-------------

  ```go
  package main
  import (
    "fmt"
    "github.com/reflexionhealth/gopdf"
  )

  func main() {

    pdf := gopdf.GoPdf{}
    pdf.Start(gopdf.Config{Unit: "pt", PageSize: gopdf.Rect{W: 595.28, H: 841.89}}) //595.28, 841.89 = A4
    pdf.AddPage()
    err := pdf.AddTTFFont("HDZB_5", "../ttf/wts11.ttf")
    if err != nil {
        log.Print(err.Error())
        return
    }

    err = pdf.SetFont("HDZB_5", "", 14)
    if err != nil {
        log.Print(err.Error())
        return
    }
    pdf.Cell(nil, "您好")
    pdf.WritePdf("hello.pdf")

  }
  ```
