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
|---------------------------|--------|
| Liquid-crystal display    | LCD    |
| --------------------------|--------|
| Thank George It's Friday! | TGIF   |


```kotlin
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
