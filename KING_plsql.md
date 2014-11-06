## PL/SQL 


### substr について
substr(data1,2,1) data1という対象文字列の２桁目から1文字抜き取る  
substrb(data1,2,1)data1という対象文字列の２桁目から1バイト抜き取る  

"あ"は２バイトなので要注意  

### カンマを含む文字列
' I'm MEGUMI ' 文字列としてIしか認識されない。

対処方
-> q'[I'm MEGUMI]'  -> ' I''m MEGUMI'



