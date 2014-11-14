# PL/SQLスニペット

## CSVの切だし処理

### シンプル版

	set serveroutput on
	declare
		procedure p(
			piv_str		in	varchar2
		)
		is
		begin
			dbms_output.put_line(piv_str);
		end ;

		function split_csv(
			piov_csv	in out	varchar2
		,	piv_delim	in		varchar2	default ','
		)
		return varchar2
		is
			wn_pos	number;
			wv_ret	varchar2(2000);
		begin
			wn_pos := instr(piov_csv, piv_delim);
			if	wn_pos = 0
			then
				wv_ret		:=	piov_csv;
				piov_csv	:=	null;
			else
				wv_ret		:=	substr(piov_csv, 1, wn_pos-1);
				piov_csv	:=	substr(piov_csv, wn_pos+1);
			end if;
			return wv_ret;
		end ;

		procedure test_split_csv(
			piv_csv	in	varchar2
		)
		is
			wv_csv	varchar2(2000)	:=	piv_csv;
			wv_str	varchar2(2000);
		begin
			p('---------------------------');
			p('split for '||wv_csv);
			while wv_csv is not null
			loop
				wv_str := split_csv(wv_csv);
				p(wv_str);
			end loop;
		end ;
	begin
		test_split_csv('aaa,aaa,bbb,xxxx,ccc');
		test_split_csv('aaa,aaa,"bbb,xxxx",ccc');
	end ;
	/

### 文字列ラップ対応版

	set serveroutput on
	declare
		procedure p(
			piv_str		in	varchar2
		)
		is
		begin
			dbms_output.put_line(piv_str);
		end ;

		function split_csv(
			piov_csv	in out	varchar2
		,	piv_delim	in		varchar2	default ','
		,	piv_wrap	in		varchar2	default '"'
		)
		return varchar2
		is
			wv_prefix	varchar2(10);
			wn_pos		number;
			wv_ret		varchar2(2000);
		begin
			if	substr(piov_csv, 1, 1) = piv_wrap
			and	instr(piov_csv|| piv_delim , piv_wrap || piv_delim) > 1
			then
				wv_prefix := piv_wrap;
			end if;

			wn_pos := instr(piov_csv, wv_prefix || piv_delim);
			if	wn_pos = 0
			then
				wv_ret		:=	piov_csv;
				piov_csv	:=	null;
			else
				wv_ret		:=	substr(piov_csv, 1 , wn_pos-1);
				piov_csv	:=	substr(piov_csv, wn_pos+1);
			end if;

			if	wv_prefix is not null
			then
				wv_ret := substr(wv_ret, 1 + length(wv_prefix));
			end if;
			return wv_ret;
		end ;

		procedure test_split_csv(
			piv_csv	in	varchar2
		)
		is
			wv_csv	varchar2(2000)	:=	piv_csv;
			wv_str	varchar2(2000);
		begin
			p('---------------------------');
			p('split for '||wv_csv);
			while wv_csv is not null
			loop
				wv_str := split_csv(wv_csv);
				p(wv_str);
			end loop;
		end ;
	begin
		test_split_csv('aaa,aaa,bbb,xxxx,ccc');
		test_split_csv('aaa,aaa,"bbb,xxxx",ccc');
	end ;
	/


