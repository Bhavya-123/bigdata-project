# bigdata-project

### What is Bigdata?

Big data as per [Wikipedia](https://en.wikipedia.org/wiki/Big_data) is a field that treats ways to analyze, systematically extract information from, or otherwise deal with data sets that are too large or complex to be dealt with by traditional data-processing application software.

---

### What are we going to do in this repo?

This repository takes you through a simple Bigdata application that allows us to count the number of words(excluding few [common words in English](https://en.wikipedia.org/wiki/Most_common_words_in_English)) in an webpage. This repo also helps you to visualize the top 10 words in the form of a chart.

#### Pre-requisites:

1. Spark to be configured - You can check the repo [https://github.com/denisecase/setup-spark](https://github.com/denisecase/setup-spark). This repo has everthing you need to setup spark with clear instructions.
2. Ability to run powershell as admin. If you would like to setup you system to be run as a professional developer, the repo [https://github.com/denisecase/windows-setup](https://github.com/denisecase/windows-setup) is a great start 
3. IDE (VSCode preferred) download here [https://code.visualstudio.com/](https://code.visualstudio.com/)
4. Basic coding knowledge of Spark. Read [https://spark.apache.org/](https://spark.apache.org/)

---
### Getting started with the word count application.

#### Getting the data for our application.

Here I am using a webpage that is out on the internet for my application and is available at [http://shakespeare.mit.edu/allswell/full.html](http://shakespeare.mit.edu/allswell/full.html).There is no restriction on the website being used.

Now that we found our data, we need to get it to our local-machine to work on it and ```curl``` helps us in grabbing the data from a ```HTML``` page to a text file. Use the command below to do so.

```curl "http://shakespeare.mit.edu/allswell/full.html" -O "allIsWell.txt"```

Now we have our website data on our local machine, but it has the HTML tags in it and needs some cleaning to be done. The ```sed``` command of ```UNIX``` is a powerful command that allows us to remove unwanted data using regex. Run the below command in ```git bash``` to remove most of the HTML tags from our data.

```sed -E 's/<[^>]*>/''/g' allIsWell.txt > allIsWell_cleaned.txt```

Now lets remove most of the common words as well using the same ```sed``` command with words to be removed.

``` sed -E 's/\b(the|The|be|Be|to|To|of|Of|And|and|a|A|in|In|that|That|have|Have|i|I|it|It|for|For|not|Not|on|On|with|With|he|He|as|As|you|You|do|Do|at|At|this|This|his|His|by|By|from|From|they|They|we|We|say|Say|her|Her|she|She|or|Or|an|but|But|will|Will|So|so|my|is|your|me|him|are|what|there|their|one|all|would|up|out|if|about|who|get|which|go)\b/''/g' allIsWell_cleaned.txt > allIsWell_final.txt```

You can do further cleaning if needed. 










