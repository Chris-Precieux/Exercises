# Exercises


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
