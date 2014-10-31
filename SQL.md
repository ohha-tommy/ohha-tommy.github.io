## SQL
  sqlplusにデータを入れる
  
  ## SQLとPL/SQLのちがい
	### SQL は

		select substr(data1, ',' , 1,1)  
		from dual  

	### PL/SQLは

		FUGA := substr(data1, ',' , 1,1)  

	### もしくは
	
		select substr(data1, ',' , 1,1)  
		into FUGA  
		from dual  

	### SQL は

		select length(data1)  
		from dual  

	### PL/SQLは  

		HOGE := length(data1)  

	### もしくは
	
		select length(data1, ',' , 1,1)  
		into HOGE  
		from dual  





  
  
  [DEFINE説明のサイト](http://www.shift-the-oracle.com/sqlplus/command/define.html)
