The first and most important thing is to know that the Python version used for the coding is:-"3.9.18".

<h1>How the segregation of data is done??</h1>
The architecture of the code follows the collection of data based on the category. So the files which include Mandatory, Optional, Logs, and inconsistent URLs are segregated based on the category. 
So for a specific category, the dataset will look like this:-

<p align="center" style="border: 2px solid red; padding: 10px;">
  <img width="746" alt="image" src="https://github.com/EESHAN-ANAND-2002/Code-Web-Scrapping-for-Industry-Buying/assets/154071757/f78e5f3f-cf04-4d89-ba01-622661a40f01">
</p>
<br>
Here, the category we collected the data is Abrasives.
<br>
Similarly for another category, Adhesives Sealants and Tape
<p align="center" style="border: 2px solid red; padding: 10px;">
<img width="503" alt="image" src="https://github.com/EESHAN-ANAND-2002/Code-Web-Scrapping-for-Industry-Buying/assets/154071757/04b43dd2-2b66-4d2b-a7e4-c9db0a47dd7d">
</p>


<hr>
<h1>The Mandatory dataset:-</h1>
Let's take a look at how mandatory data looks for each category:-
<p align="center" style="border: 2px solid red; padding: 10px;">
<img width="1376" alt="image" src="https://github.com/EESHAN-ANAND-2002/Code-Web-Scrapping-for-Industry-Buying/assets/154071757/25501fbc-b146-430c-8e7e-a1c4fc22bda0"></p>
Let's see what each column is about:-
Let's see what each column is about:
# Unordered list

* Primary Key <br>
* Brand <br>
* Category Listing from L1 to L6-L1 shows the main category, L2 shows the sub-category(it is listed else blank), and the rest of the category is mentioned if it is present in the product's listing. <br>
* Product- gives the product a user would expect such as combs, toothpaste, etc. The main thing is that the website listing for this product is very specific, so please consider generalization in the data preprocessing part.<br>
* Name- represents the name of the product.<br>
* Peice Quantity- Some of the websites sell the products in pieces rather than individually. So if a person purchased one unit, they won't get an individual item, but in pieces of it. For eg- When you buy "thumb tacks", you won't be possibly buying a single one but a whole collection of it or in pieces. The current website where we are collecting the data is "IndustryBuying", so in every single scenario, the Peice Quantity is one. It might be different on different websites.<br>
* MRP- represents the MRP of the product without the discount.<br>
* Discount Price(Max), and Discount Price(Min)- these both represent the range of discounts we can get from buying the product, it is seen that the more bundles of products a user buys, the better the discount. The Discount Price(Max) is the Discount Price that represents less discount given, and the Discount Price(Min) represents the maximum discount given.<br>

* Discount Check- <b>has value varies from 0 to 3</b>:-
    * 0-Represents no discount is given on the product, either you buy a single unit or in bundles.<br>
    * 1-Represents discounts only on individual products. For the rest, if you buy more bundles, then an exclusive discount won't be given it will be applied and will be the same for each as listed for the individual.<br>
    * 2-Represents exclusive discount is present only if the products are bought in bundles rather than individuals.<br>
    * 3-Represents discount will be given individually as well as exclusively for bundles.<br>
* URL-mentions the URL of the product.
<hr>
<hr>
<h1>The Optional Dataset:-</h1>
The optional dataset looks like this:-<br>
<b>Here the important thing to note is, that the "Model no" will be the same as the "Primary Key". So whenever the data merging is there, we will be taking the help of these keys.</b>
<p align="center" style="border: 2px solid red; padding: 10px;">
<img width="1248" alt="image" src="https://github.com/EESHAN-ANAND-2002/Code-Web-Scrapping-for-Industry-Buying/assets/154071757/c9b94338-5cb1-4f01-b00a-7bff450d1132">
</p>
There are two things to note:-<br>
* The "Model no" uniquely identifies a product.<br>
* The rest of the item represent the quality or the attributes of the product.<br>
<hr>
<hr>
<h1>The Logs:-</h1>
The logs look something like this:-
<p align="center" style="border: 2px solid red; padding: 10px;">
<img width="760" alt="image" src="https://github.com/EESHAN-ANAND-2002/Code-Web-Scrapping-for-Industry-Buying/assets/154071757/bfb5042b-6d3a-4b36-bd3f-80cf191b176f">
</p>
In the log, each data point is segregated with a sub-category present in that specific category. See whenever we collect data for each category, we visit each sub-category and the sub-category is divided into pages. To access, all the products from the sub-category, we have to access all the pages. Due to this, a specific sub-category or some pages from that sub-category may fail to access due to some network issue or inconsistency in the website. So we list that problem here in the logs:-<br>
# Unordered list

* Category URL-has the URL of the category from where the sub-categories are collected. For logs in a specific category, the category URL will be the same for all data points.
* Sub Category URL- has the URL of all the sub-categories mentioned in the category
* Category- represents the name of the category. Here it is:-"Agriculture Garden & Landscaping".
* Sub Category- represents the name of the sub-category present in the category.
* Category Shows whether the URL having the Category is retrieved.
* Sub Category Check shows whether the URL of the sub-category is retrieved. Here all the sub-categories are retrieved so the value of the check is 0 in all cases.
* Pages Check- shows whether all the pages are retrieved from the sub-category. In case, some of the pages are not collected(even 1), it shows the check as 1, eg:- in the second last instance, page 3 was not retrieved, so for that the Pages Check is set to 1.
* Pages Not Retrieved-shows all the pages that weren't retrieved during the data collection process.
* Total Products- shows all the products that are present in the Sub-Category section. There could be some URLs that are duplicates due to some inconsistency in the website or product repetitions. That is handled in the next column named "Non-Duplicated Products".
* Non Duplicated Products- has all the unique product URLs. Enjoy!!

<h3>Now consider a scenario where we fail to collect the category:-</h3>
In that case, we will have a single dataset "logs" for that specific category. <b>Please don't confuse the category name with the actual category name on the website. This is just a dummy variable that is used for testing.</b><br>
<p align="center" style="border: 2px solid red; padding: 10px;">
<img width="566" alt="image" src="https://github.com/EESHAN-ANAND-2002/Code-Web-Scrapping-for-Industry-Buying/assets/154071757/6f2bc174-4e09-4dd0-a153-77e0262be809">
</p>

This dataset will only have information about the category URL and the name of the category. Since we have failed to extract it, we can't find what's inside it or what are sub-categories present in it.<br> 
<img width="732" alt="image" src="https://github.com/EESHAN-ANAND-2002/Code-Web-Scrapping-for-Industry-Buying/assets/154071757/340e5353-e1bf-4ee8-b013-d948e574e105">
<hr>
<hr>
<h1>The InconsistenProduct dataset:-</h1>
It has a URL for every single product which were failed to be retrieved from the specific category.
<p align="center" style="border: 2px solid red; padding: 10px;">
<img width="310" alt="image" src="https://github.com/EESHAN-ANAND-2002/Code-Web-Scrapping-for-Industry-Buying/assets/154071757/0c60c263-0d87-44ce-af71-c3ff67bfd883">
</p>
<hr>
<hr>
<h1>Overall_logs</h1>:-
This is a folder that contains the dataset of "summarised_InconsistentProducts" and "summarised_logs" which contains every log and inconsistent dataset in the main directory.
