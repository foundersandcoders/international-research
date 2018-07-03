

____________________________
## What is RegEx
* A regular expression (regex or regexp for short) is a special text string for describing a search pattern so it works only on string data types
https://regexone.com/lesson/introduction_abcs

* Regular expressions are extremely useful in extracting information from text such as code

* Characters include normal letters, but digits as well. In fact, numbers 0-9 are also just characters 

* examples of Regex

  * Match	abc123xyz	Success
  * Match	define "123"	Success
  * Match	var g = 123;	Success

myreg = /123/--> matches all the above strings





_________________________













## Some RegEx Methods



**search() method :**

search method returns the first index that contain the string you are searching for :
> var str = "Founders&Coders";
> var n = str.search(/&C/i);
> 
 n will be 8
________



**replace method:**
.replace();

example1:
 cleaning a string 

> function removeNoise(str){
>   if (str.length==0) return ''; <br>
> 	var s=str.replace(/[%$&/#·@|º\\ª]/g, '');
>   return s ;
> }
> 

example2:
 mistakes corrections
> function CorrectMe(str){
>   if (str.length==0) return '';
> 	var s=str.replace(/[gogle]/g, 'google');
>   return s ;
> }





**test() method:**
return true or false
check if a string contains another string
example
> /Shawerma/.test("I Love Shawerma");
> 
will return true 


________


https://www.rexegg.com/regex-quickstart.html

____






## Useful regex Tools

https://regex101.com/ is very useful. 



## How to validate an email address
##### Ben Will Explain  Using Regex101.com
[A-Za-z0-9_\\-\\.]{1,}\\@[A-Za-z]{1,20}\\.[A-Za-z]{2,3}\\.[A-Za-z]{2,3}

This only works for emails ending in .**.**, not .***
