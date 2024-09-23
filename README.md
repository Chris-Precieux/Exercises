# Exercises

## Exercise 1: Acronym

Convert a phrase to its acronym.

Techies love their TLA (Three Letter Acronyms)!

Help generate some jargon by writing a program that converts a long name like Portable Network Graphics to its acronym (PNG).

Punctuation is handled as follows: hyphens are word separators (like whitespace); all other punctuation can be removed from the input.

For example:

| Input                     | Output |
|---------------------------|--------|
| As Soon As Possible       | ASAP   |
|                           |        |
| Liquid-crystal display    | LCD    |
|                           |        |
| Thank George It's Friday! | TGIF   |


```kotlin
// @Author -> Doctor Night

fun main() {
    val names: List<String> = listOf(
        "As Soon As Possible", 
        "Liquid-crystal display", 
        "Thank George It's Friday!")
    
    val acronyms: MutableList<String> = mutableListOf()
    
    for(name in names) {
        var characters: String = ""
        
        if(name.contains("-")) {
          val newValue = name.replace("-", " ")
          val split = newValue.split(" ")
          
          for(acronym in split) {
          	characters = "$characters${acronym[0]}"
          } 
          
        } else {
        	val split = name.split(" ")
        
            for(acronym in split) {
                characters = "$characters${acronym[0]}"
            }    
        }

        acronyms.add(characters.toUpperCase())
    }
    
    print(acronyms)
    	
}

```




## Exercise 2

An Armstrong number is a number that is the sum of its own digits each raised to the power of the number of digits.

For example:

* 9 is an Armstrong number, because 9 = 9^1 = 9
* 10 is not an Armstrong number, because `10 != 1^2 + 0^2 = 1`
* 153 is an Armstrong number, because: `153 = 1^3 + 5^3 + 3^3 = 1 + 125 + 27 = 153`
* 154 is not an Armstrong number, because: `154 != 1^3 + 5^3 + 4^3 = 1 + 125 + 64 = 190`
* Write some code to determine whether a number is an Armstrong number.

```kotlin

// @Author -> Doctor Night

import kotlin.math.pow;

fun Int.nbDigits(): Int { // -> extension function
	return this.toString().length
}


fun Int.eachDigit(): List<Int> { // -> extension function
    val listOfDigits: MutableList<Int> = mutableListOf();
    
    for(index in 0 until nbDigits()) {
        listOfDigits.add(Character.getNumericValue(toString()[index]))
    }
    
    return listOfDigits
}


fun main() {
    
    val	numbers: List<Int> = listOf(123, 39, 153, 90, 9)
      
    for(number in numbers) {
        var sum = 0.0;
        
        for(digit in number.eachDigit()) {
        	sum += digit.toDouble().pow(number.nbDigits())
        }
        
        println(sum.toInt().also { 
            when(it == number) {
                true -> print("✅ ")
                else -> print("❌ ")
            }
        	
            
        })
    }
}

```
