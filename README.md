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
* **affectedProduct** - List of prodcuts affected by this drug shortage.
  * **discontinued**: Bool - Whether this product has been discontinued.
  * **NDC**: String - National Drug Code identifier for this product. 
  * **RXCUI**: String - RXCUI identifier for this product
  * **textDescription**: String - Human readable text description of this product.
  
* **availableProduct** - List of available products for this drug shortage.
  * **NDC**: String - National Drug Code identifier for this product. 
  * **RXCUI**: String - RXCUI identifier for this product
  * **textDescription**: String - Human readable text description of this product.
  
* **lastRevisedDate**: String - Human readable time stamp of the last revision.

* **patientCareImplications**: [String] - List of patient care implications.

* **resupplyEstimateNote**: [String] - List of resuply estimate notes.

* **safetyNote**: [String] - List of safety notes.

* **searchString**: String - A string to help run search queries. 

* **shortageAuthor**: [String] - List of authors for this drug shortage.

* **shortageCreateDate**: String - Human readable timestamp for creation of this shortage data.

* **shortageReason**: [String] - List of reasons that cauased this shortage. 

* **shortageStatus**: String - Status of a drug shortage. This property has an enum for defined values: 
  * "Active", "Resolved", "No Longer Available", "No Commercially Available Preparations"
  
* **shortageTitle**: String - Title for this shortage

* **shortageVersion**: String - Revision version of this shortage. This can be converted to an Integer. 

* **updatedAt**: Int - Linux epoch timestamp in milliseconds of the last update. This is the best field for time based sorting.

* **updateHistory**: String - Human readable update history.

## JSON Sample of Drug shortage object
---
* route: https://ahfs.firebaseio.com/drugShortages/101/latest.json
* response value:

{"affectedProduct":[{"NDC":"17478-0934-01","RXCUI":"966571","discontinued":"true","textDescription":"Hydralazine injection, Akorn, 20 mg/mL, 1 mL vial, 10 count, NDC 17478-0934-01"},{"NDC":"00517-0901-25","RXCUI":"966571","textDescription":"Hydralazine injection, American Regent, 20 mg/mL, 1 mL vial, 25 count, NDC 00517-0901-25"}],"availableProduct":[{"NDC":"17478-0934-15","RXCUI":"966571","textDescription":"Hydralazine injection, Akorn, 20 mg/mL, 1 mL vial, 25 count, NDC 17478-0934-15"},{"NDC":"63323-0614-01","RXCUI":"966571","textDescription":"Hydralazine injection, Fresenius Kabi, 20 mg/mL, 1 mL vial, 25 count, NDC 63323-0614-01"},{"NDC":"39822-0500-04","RXCUI":"966571","textDescription":"Hydralazine injection, X-Gen, 20 mg/mL, 1 mL vial, 25 count, NDC 39822-0500-04"}],"lastRevisedDate":"06-Jun-2017","resupplyEstimateNote":["American Regent has hydralazine 20 mg/mL 1 mL vials on back order and the company cannot estimate a release date.","All other marketed presentations are available."],"searchString":"hydralazine injection","shortageAuthor":["Michelle Wheeler"],"shortageCreateDate":"29-Jun-2015","shortageReason":["Akorn has hydralazine injection available.","American Regent has hydralazine injection on shortage due to manufacturing delays. This product has not been available for several years.","Fresenius Kabi has hydralazine injection available.","X-Gen launched hydralazine injection in September 2015."],"shortageStatus":"Resolved","shortageTitle":"Hydralazine Injection","shortageVersion":"18","updateHistory":"Updated June 6, 2017 by Michelle Wheeler, PharmD, Drug Information Specialist. Created September 12, 2014 by Michelle Wheeler, PharmD, Drug Information Specialist. Copyright 2017, Drug Information Service, University of Utah, Salt Lake City, UT.","updatedAt":1496776133234}


  


