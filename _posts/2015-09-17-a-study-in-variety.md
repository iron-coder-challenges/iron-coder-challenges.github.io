---
layout: post
title: Fizz Buzz - A Study in Variety
categories: Review
---

*Iron Coder Premiere*

_Fizz Buzz in your choice of language_

This past week the Iron Coder team started up here at CodeNewbie. This is a team that tackles coding challenges in the language of their choice. Our first project is winding down to a close and we have had great participation in a wonderfully wide variety of languages.

## How to solve Fizz Buzz

The basic idea behind Fizz Buzz is to take a series of numbers and perform replacements on them before outputting them.  If the number is divisible by 3, replace it with the word "Fizz".  If the number is divisible by 5, replace it with the word “Buzz”.  If it is divisible by both, replace it with “FizzBuzz”.

### Modulo

To determine if an integer is evenly divisible by another integer, a mathematical operation called modulo is used.  Modulo is often represented by the "%" character, while division is represented by “/”.  This modulo operation, returns the result not of the division itself, but of the remainder after division has been performed. To better understand this, consider the following:

12 / 3 = 4
13 / 3 = 4 Remainder 1
14 / 3 = 4 Remainder 2
15 / 3 = 5

Above you can see that 12 and 15 can be evenly divisible by 3, leaving no remainder.  When you divide 13 or 14 by 3 you have a remainder of 1 and 2, respectively

It follows that when you use the modulo operation you get the following results:

12 % 3 = 0
13 % 3 = 1
14 % 3 = 2
15 % 3 = 0

Where the result of the modulo operation is the remainder left over from the integer division.

### General Logic

With the modulo operation in hand the rest of the solution falls into place.  The general logic of the solution will be a variation on the following:

Loop through a series of numbers

	If the number modulo 3 equals 0 output fizz
	If the number modulo 5 equals 0 output buzz
	If both modulo 3 and 5 equals 0 output fizzbuzz
	If none of the above are true, output the number

End Loop

## Language Agnosticism

One of the things that I am really enjoying about this first exercise is the wide variety of languages that solutions have been submitted in. We have solutions in the following list of languages:

* C
* C++
* Clojure
* Go
* Perl
* Assembly (via g++ compiler)
* PHP
* Javascript
* Java
* Ruby
* Python

I have enjoyed going between these solutions and comparing them not only for the logic and syntax choices made by the developer, but also the choices made by the languages that the solutions are written in.

## Examples

Let's take a closer look at a few of the solutions to see how they differ and how they are the same.

### Javascript

I enjoy the way that Kim Still has used functions to organize the conditional logic that determines which value is output. It is very readable and there is a strong sense of organization in the code.

{% highlight js %}

var string = "";

var fizz = function() {
  if (i % 3 === 0) {
    fizzbuzz(i);
  } else {
    buzz(i);
  }
};

var buzz = function () {
  if ((i % 5) === 0) {
    string += "Buzz ";
  } else {
    string += i + " ";
  }
};

var fizzbuzz = function () {
  if ((i % 5) === 0) {
    string += "FizzBuzz ";
  } else {
    string += "Fizz ";
  }
}

for (i = 1; i <= 100; i++) {
  fizz(i);
};

console.log(string);

{% endhighlight %}

### C

Derek Gustafson’s C based solution uses a switch statement along with a clever logic involving the values resulting from modulo 15, the sum of 3 and 5.  The switch statement picks out all of the significant modulo values and defaults the rest to the original number.

{{ highlight c }}

int main(void)
{
	int i;

	for(i=1; i<101; i++)
	{
		switch(i % 15)
		{
			case 0:
				printf("fizzbuzz\n");
				break;
			case 5:
			case 10:
				printf("buzz\n");
				break;
			case 3:
			case 6:
			case 9:
			case 12:
				printf("fizz\n");
				break;
			default:
				printf("%d\n", i);
		}
	}
	return 0;
}

{{ end highlight }}

## PHP

PHP is a scripting language used to generate dynamic web content, it was one of the first languages of the web and it is still widely used today.  Keyasha Brothern provided the following solution in PHP.

<?php

for($i = 1; $i <= 100; $i++) {
   if ($i % 3 == 0 && $i % 5 == 0) {
    echo "FizzBuzz\n";
    } elseif ($i % 3 == 0) {
        echo "Fizz\n";
    } elseif ($i % 5 ==0) {
        echo "Buzz\n";
    }else{
        echo "$i\n";
    }
}

## Clojure

Clojure is a language that brings together the power of Lisp with the reliable portability of the Java Virtual Machine. It is a language that looks the most foreign to me, and that makes me want to learn more about it.  Derek Gustafson was kind enough to write the following Fizz Buzz solution in Clojure.

(ns fizz-buzz.core
  (:gen-class))

(defn fb_test [x]
  (cond
    (= (mod x 15) 0) "fizzbuzz"
    (= (mod x 3) 0) "fizz"
    (= (mod x 5) 0) "buzz"
    :else x))

(defn fb_print [x] (println (fb_test x)))

(defn -main
  [& args]
  (dotimes [n 100] (fb_print (+ n 1))))

## Go

André Almar wrote the following solution in Go. The Go language is a relative newcomer and this is the first time that I have had a chance to see an example of Go code. Again you see differences from other languages, for instance the for loop that acts more like a traditional while() loop as it does not increment the counter.

package main

import (
        "fmt"
)

func main(){
  number := 1
  for number <= 100 {
    if number % 3 == 0 && number % 5 == 0 {
        fmt.Println("FizzBuzz")
    } else if number % 3 == 0 {
        fmt.Println("Fizz")
    } else if number % 5 == 0{
        fmt.Println("Buzz")
    } else {
        fmt.Println(number)
    }

    number += 1
  }
}

## Conclusion

I am thrilled to have this opportunity to work with Iron Coders that have such a diverse set of coding backgrounds.  This first week they have provided a set of solutions to the Fizz Buzz challenge that exemplify two of the things that I enjoy about this project. These are the different ways that people approach the same problem and the ways that different languages shape the ways that we solve those problems.

All of the solutions submitted were great and I appreciate the team members taking the time to work on them.  I hope that you all have a chance to look through the solutions below to see for yourselves the work that they have done.

## Solutions

**André Almar**

**[https://github.com/andrealmar/ironcode**r](https://github.com/andrealmar/ironcoder)

**Derek Gustafson**

**[https://github.com/degustaf/Iron_Coder_00**1](https://github.com/degustaf/Iron_Coder_001)

**Jonathan Colon **

**[https://github.com/jcode89/Iron_Coder_Solution**s](https://github.com/jcode89/Iron_Coder_Solutions)

**Keyasha Brothern**

**[https://github.com/KMBrothern/iron_code**r](https://github.com/KMBrothern/iron_coder)

**Kim Still**

**[https://github.com/twomoredays/Iron-Coder/tree/master/01%20-%20FizzBuz**z](https://github.com/twomoredays/Iron-Coder/tree/master/01%20-%20FizzBuzz)

**Victor Keenan **

**[https://github.com/VictorSK/Iron_Code**r](https://github.com/VictorSK/Iron_Coder)

**Valerie Sharp**

**[https://github.com/valerie937/FizzBuz**z](https://github.com/valerie937/FizzBuzz)

**Jamal Hansen**

**[https://github.com/jamalhansen/ic001-fizz-buz**z](https://github.com/jamalhansen/ic001-fizz-buzz)

## References

Modulo - [https://en.wikipedia.org/wiki/Modulo_operation](https://en.wikipedia.org/wiki/Modulo_operation)

How to Solve Fizz Buzz - [http://www.codenewbie.org/blogs/how-to-solve-fizzbuzz](http://www.codenewbie.org/blogs/how-to-solve-fizzbuzz)

Iron Coder Premiere - [https://www.youtube.com/watch?v=z7D1NxLxuPA](https://www.youtube.com/watch?v=z7D1NxLxuPA)

