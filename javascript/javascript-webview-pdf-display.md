# PDF View Display

네이티브 웹앱에서 PDF 다운로드가 안되는 이슈로, PDF를 보여줘야 하는 이슈 발생

PDF를 보여줘야 하는 다양한 방법 중, 앱 화면 유지를 위해 서브팝업 형식으로 열고 닫고 기능을 하도록 적용

## iFrame
iFrame으로 PDF를 출력하는 방법으로 진행


* <1안> IFRAME 이용

```js
<iframe src="http://홈페이지주소/test.pdf" style="width:70px; height:700px;" frameborder="0"></iframe>
```

* <2안> - 구글뷰어 이용

```js
<iframe src="http://docs.google.com/gview?url=http://홈페이지주소/test.pdf&embedded=true" style="width:70px; height:700px;" frameborder="0"></iframe>
```

* <3안> - OBJECT 이용

```js
<object type="application/pdf" data="http://홈페이지주소/test.pdf" width="700" height="800">
<param name="src" value="http://홈페이지주소/test.pdf">
</object>
```

> 3가지 방법을 모두 적용해 봤지만, 이슈발생
> iFrame으로 PDF를 출력시 iOS는 출력이 안되는 자앵 발생

## Emebed
iOS에서는 iFrame 적용이 안되서 임베디드로 PDF 출력을 시도

```js
<object data="your_url_to_pdf" type="application/pdf">
    <embed src="your_url_to_pdf" type="application/pdf" />
</object>
```

드디어
PDF가 출력이 되지만, 첫페이지만 출력이 되는 장애.



# Libary
iFrame, Embed로 해결이 안되, PDF View 라이브러리 관련 자료 검색해보니, 2가지 좋은 라이브러리 발견

1. [PDFObject](https://pdfobject.com/#examples)
2. [PDF.js](https://mozilla.github.io/pdf.js/)

## PDF Object Js
https://pdfobject.com/#examples


## PDF.js
https://mozilla.github.io/pdf.js/
