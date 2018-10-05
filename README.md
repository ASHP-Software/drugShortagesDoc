# Drug Shortages Documentation

## Drug shortage routes
---

* **/drugShortages** - This route holds all the latest version of each drug shortage.
  * **/drugShortages/{key}/latest** - This route holds an individual drug shortage. You can assume that it will always be the latest version of the data. 


* **/pastDrugShortages** - This route holds all the previous version of each drug shortage. Each time an editor makes a change to a drug shortage bulletin in their local content management system and commit the changes, a new versiosn of a drug shortage object is created and pushed to Firebase.
  * **/pastDrugShortages/{key}/{versionKey}** - This route holds a unique version of a drug shortages. The key will always be an Int value. A higher value indicates a more recent revision of the shortage data.
  
## Drug shortage object
---
### Drug Shortage
A drug shortage bulletin that holds all relevant information.
* **affectedProduct** - List of prodcuts affected by this drug shortage
  * **discontinued**: Bool - Whether this product has been discontinued by the manufacturer
  * **NDC**: String - National Drug Code identifier for this product. 
  * **RXCUI** - RXCUI identifier for this product


  


