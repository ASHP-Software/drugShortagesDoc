# ASHP Drug Shortages Documentation

## Drug shortage routes
---

Keep in mind that if you are making a REST API call, you need to append .json to the end of the route. You can find some sample API calls at the end of this document.

* **/drugShortages** - This route holds all the latest version of each drug shortage returned as an array. The ID / key for each shortage object is the same as its index in the array. Some entries may be null, which means there is no shortage with that ID.
  * **/drugShortages/{key}/latest** - This route holds an individual drug shortage. You can assume that it will always be the latest version of the data.


* **/pastDrugShortages** - This route holds all the previous version of each drug shortage. Each time an editor makes a change to a drug shortage bulletin in their local content management system and commit the changes, a new versiosn of a drug shortage object is created and pushed to Firebase.
  * **/pastDrugShortages/{key}/{versionKey}** - This route holds a unique version of a drug shortages. The key will always be an Int value. A higher value indicates a more recent revision of the shortage data.
  
## Objects
---
### Drug Shortage
A drug shortage bulletin that holds all relevant information.
* **affectedProduct** - List of prodcuts affected by this drug shortage. Affected products are the actual product on shortage (at the NDC (package size) level).
  * **discontinued**: Bool - Whether this product has been discontinued.
  * **NDC**: String - National Drug Code identifier for this product. 
  * **RXCUI**: String - RXCUI identifier for this product
  * **textDescription**: String - Human readable text description of this product.
  
* **availableProduct** - List of available products for this drug shortage.  Available products are same drug that is on shortage, but maybe in a different strength or package size.
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

* **shortageReason**: [String] - List of reasons that caused this shortage. 

* **shortageStatus**: String - Status of a drug shortage. This property has an enum for defined values: 
  * "Active", "Resolved", "No Longer Available", "No Commercially Available Preparations"
  
* **shortageTitle**: String - Title for this shortage

* **shortageVersion**: String - Revision version of this shortage. This can be converted to an Integer. 

* **updatedAt**: Int - Linux epoch timestamp in **milliseconds** of the last update in UTC. This is the best field for time based sorting. You may need to multiply or divide by 1000 if your system keeps Epoch time in seconds instead of milliseconds.

* **updateHistory**: String - Human readable update history.

* **alternativeAgent**: [String] - Different drugs that are in the same therapeutic category as the drug on shortage.

* **alternativeAgentTable**: [String] - List of tables in html formated String. 

## Sample response of a drug shortage object
---
* route: /drugShortages/113/latest.json?auth={apiKey}
* To request an API key and licensing information, contact softwaresupport@ashp.org
* response:
```javascript
{
  "affectedProduct" : [ {
    "NDC" : "47781-0583-68",
    "RXCUI" : "860092",
    "textDescription" : "Ketorolac injection, Alvogen, 15 mg/mL, 1 mL vial, 25 count, NDC 47781-0583-68"
  }, {
    "NDC" : "47781-0584-68",
    "RXCUI" : "1665461",
    "textDescription" : "Ketorolac injection, Alvogen, 30 mg/mL, 1 mL vial, 25 count, NDC 47781-0584-68"
  }, {
    "NDC" : "00548-9021-00",
    "RXCUI" : "1665461",
    "textDescription" : "Ketorolac injection, Amphastar, 30 mg/mL, 1 mL vial, 10 count, NDC 00548-9021-00"
  }, {
    "NDC" : "70860-0700-02",
    "RXCUI" : "860092",
    "textDescription" : "Ketorolac injection, Athenex, 15 mg/mL, 1 mL vial, 25 count, NDC 70860-0700-02"
  }, {
    "NDC" : "63323-0162-01",
    "RXCUI" : "1665461",
    "textDescription" : "Ketorolac injection, Fresenius Kabi, 30 mg/mL, 1 mL vial, 25 count, NDC 63323-0162-01"
  }, {
    "NDC" : "00409-2288-31",
    "RXCUI" : "1665675",
    "discontinued" : "true",
    "textDescription" : "Ketorolac injection, Pfizer, 15 mg/mL, 1 mL Carpuject syringe, 10 count, NDC 00409-2288-31"
  }, {
    "NDC" : "00409-3793-01",
    "RXCUI" : "860092",
    "textDescription" : "Ketorolac injection, Pfizer, 15 mg/mL, 1 mL vial, 25 count, NDC 00409-3793-01"
  }, {
    "NDC" : "00409-2287-31",
    "RXCUI" : "1665679",
    "textDescription" : "Ketorolac injection, Pfizer, 30 mg/mL, 1 mL Carpuject syringe, 10 count, NDC 00409-2287-31"
  }, {
    "NDC" : "00409-2287-23",
    "RXCUI" : "1665679",
    "textDescription" : "Ketorolac injection, Pfizer, 30 mg/mL, 1 mL iSecure syringe, 10 count, NDC 00409-2287-23"
  }, {
    "NDC" : "00409-3795-01",
    "RXCUI" : "1665461",
    "textDescription" : "Ketorolac injection, Pfizer, 30 mg/mL, 1 mL vial, 25 count, NDC 00409-3795-01"
  }, {
    "NDC" : "00409-2287-61",
    "RXCUI" : "1665682",
    "textDescription" : "Ketorolac injection, Pfizer, 30 mg/mL, 2 mL for intramuscular use Carpuject syringe, 10 count, NDC 00409-2287-61"
  }, {
    "NDC" : "25021-0700-01",
    "RXCUI" : "860092",
    "textDescription" : "Ketorolac injection, Sagent, 15 mg/mL, 1 mL vial, 25 count, NDC 25021-0700-01"
  }, {
    "NDC" : "25021-0701-01",
    "RXCUI" : "1665461",
    "textDescription" : "Ketorolac injection, Sagent, 30 mg/mL, 1 mL vial, 25 count, NDC 25021-0701-01"
  }, {
    "NDC" : "25021-0701-02",
    "RXCUI" : "1665459",
    "textDescription" : "Ketorolac injection, Sagent, 30 mg/mL, 2 mL for intramuscular use vial, 25 count, NDC 25021-0701-02"
  }, {
    "NDC" : "00641-6041-25",
    "RXCUI" : "860092",
    "textDescription" : "Ketorolac injection, West-Ward, 15 mg/mL, 1 mL vial, 25 count, NDC 00641-6041-25"
  }, {
    "NDC" : "00641-6042-25",
    "RXCUI" : "1665461",
    "textDescription" : "Ketorolac injection, West-Ward, 30 mg/mL, 1 mL vial, 25 count, NDC 00641-6042-25"
  }, {
    "NDC" : "00641-6043-25",
    "RXCUI" : "1665459",
    "textDescription" : "Ketorolac injection, West-Ward, 30 mg/mL, 2 mL for intramuscular use vial, 25 count, NDC 00641-6043-25"
  } ],
  "alternativeAgent" : [ "No single agent can be substituted for ketorolac injection. The choice of alternative agent must be patient-specific, procedure-specific, and based on the clinical situation and other comorbid conditions. Utilize stakeholder clinicians to help make specific plans for individual patient populations.", "Tables 1 and 2 summarize the differences between some potential alternatives to ketorolac for acute pain. Injectable diclofenac was recently approved by the FDA (December 2014) but the product is not currently available and not included in the tables.[6,13-18] ", "During this shortage, ensure appropriate pain control and explore all therapeutic modalities. Utilize oral and rectal medications whenever possible." ],
  "alternativeAgentTable" : [ "<table style=\"border-collapse: collapse; font-family: Arial,Helvetica,sans-serif; font-size: 0.9em;\"><caption style=\"text-align: left; padding-left: 7px; font-weight: bold;\">Table 1.  Comparison of Select Non-Opioid Injectable Agents Used for Acute Pain<span style=\"font-size: 10px; vertical-align: top;\">13-16,18-19</span> </caption><thead><tr><th style=\"padding: 5px 7px; border: 1px solid black;\"><span style=\"font-weight: bold;\">Medication</span>null</th><th style=\"padding: 5px 7px; border: 1px solid black;\"><span style=\"font-weight: bold;\">Description</span>null</th><th style=\"padding: 5px 7px; border: 1px solid black;\"><span style=\"font-weight: bold;\">Labeled Indication for Adults</span>null</th><th style=\"padding: 5px 7px; border: 1px solid black;\"><span style=\"font-weight: bold;\">How Supplied</span>null</th><th style=\"padding: 5px 7px; border: 1px solid black;\"><span style=\"font-weight: bold;\">Storage and Handling</span>null</th><th style=\"padding: 5px 7px; border: 1px solid black;\"><span style=\"font-weight: bold;\">Dose Preparation</span></th></tr></thead><tbody><tr><td style=\"padding: 5px 7px; border: 1px solid black;\">Ketorolac</td><td style=\"padding: 5px 7px; border: 1px solid black;\">Nonsteroidal anti-inflammatory (NSAID)</td><td style=\"padding: 5px 7px; border: 1px solid black;\">Moderate to severe pain that requires analgesia at opioid level; for short-term use only (&lt; 5 days).</td><td style=\"padding: 5px 7px; border: 1px solid black;\">Injection: 15 mg in1 mL single-dose vial or syringe 30 mg in 1 mL single-dose vial or syringe 60 mg in 2 mL single-dose vial (30 mg/mL) <br /><br />Intranasal: 15.75 mg/spray<br /><br />Oral: 10 mg tablet</td><td style=\"padding: 5px 7px; border: 1px solid black;\">Store at room temperature (20-25 degrees C). <br /><br />Protect from light.</td><td style=\"padding: 5px 7px; border: 1px solid black;\">Withdraw the correct dose from vial into appropriate sterile syringe. Discard unused portion of single-dose vials.<br /><br />To avoid precipitation, do not mix ketorolac with morphine, meperidine, promethazine, or hydroxyzine in a syringe or other small volume. <br /><br />An intravenous bolus is given over 15 seconds.</td></tr><tr><td style=\"padding: 5px 7px; border: 1px solid black;\">Ibuprofen (Caldolor) Cumberland Pharmaceuticals</td><td style=\"padding: 5px 7px; border: 1px solid black;\">Nonsteroidal anti-inflammatory</td><td style=\"padding: 5px 7px; border: 1px solid black;\">Mild to moderate pain.<br /><br />Moderate to severe pain with adjunctive opioids.<br /><br />Fever reduction.</td><td style=\"padding: 5px 7px; border: 1px solid black;\">Injection: 100 mg/mL 8 mL single-dose vial<br /><br />Oral: multiple presentations</td><td style=\"padding: 5px 7px; border: 1px solid black;\">Diluted solutions stable for &lt;24 hours at room temperature. <br /><br />Store unopened vials at room temperature (20-25 degrees C). </td><td style=\"padding: 5px 7px; border: 1px solid black;\">Prior to administration, dilute to &lt; 4mg/mL concentration, in 0.9% sodium chloride injection, 5% dextrose injection, or lactated Ringer&#39;s injection.<br /><br />Infusion time must be no less than 30 minutes.</td></tr><tr><td style=\"padding: 5px 7px; border: 1px solid black;\">Acetaminophen (Ofirmev) Cadence Pharmaceuticals</td><td style=\"padding: 5px 7px; border: 1px solid black;\">Non-salicylate, non-opioid agent with antipyretic and analgesic effects</td><td style=\"padding: 5px 7px; border: 1px solid black;\">Mild to moderate pain.<br /><br />Moderate to severe pain with adjunctive opioids.<br /><br />Fever reduction.</td><td style=\"padding: 5px 7px; border: 1px solid black;\">Injection: 10 mg/mL 100 mL single use vial<br /><br />Oral: multiple presentations<br /><br />Rectal: multiple presentations</td><td style=\"padding: 5px 7px; border: 1px solid black;\">Store at room temperature (20-25 degrees C). <br /><br />Do not refrigerate or freeze. <br /><br />Use within 6 hours of opening the vial.</td><td style=\"padding: 5px 7px; border: 1px solid black;\">Do not mix or administer with other medications.<br /><br />Doses of 1000 mg may be given undiluted from original vial using vented IV set.<br /><br />Doses of &lt;1000 mg must be withdrawn from original vial and placed in a separate empty container (glass bottle, plastic IV container, or syringe) prior to administration. Discard unused portion of vial.<br /><br />Infusion time is 15 minutes.</td></tr></tbody></table>", "<table style=\"border-collapse: collapse; font-family: Arial,Helvetica,sans-serif; font-size: 0.9em;\"><caption style=\"text-align: left; padding-left: 7px; font-weight: bold;\">Table 2. Comparison of Non-Opioid Injectable Agents Used for Acute Pain: Pharmacokinetic Parameters, Warnings and Contraindications <span style=\"font-size: 10px; vertical-align: top;\">13-19</span> </caption><thead><tr><th style=\"padding: 5px 7px; border: 1px solid black;\"><span style=\"font-weight: bold;\">Medication</span>null</th><th style=\"padding: 5px 7px; border: 1px solid black;\"><span style=\"font-weight: bold;\">Mean Volume of Distribution</span>null</th><th style=\"padding: 5px 7px; border: 1px solid black;\"><span style=\"font-weight: bold;\">Mean Half-life</span>null</th><th style=\"padding: 5px 7px; border: 1px solid black;\"><span style=\"font-weight: bold;\">Protein binding</span>null</th><th style=\"padding: 5px 7px; border: 1px solid black;\"><span style=\"font-weight: bold;\">Black Box Warnings</span>null</th><th style=\"padding: 5px 7px; border: 1px solid black;\"><span style=\"font-weight: bold;\">Contraindications</span></th></tr></thead><tbody><tr><td style=\"padding: 5px 7px; border: 1px solid black;\">Ketorolac</td><td style=\"padding: 5px 7px; border: 1px solid black;\">Intravenous: 0.21 L/kg<br /><br />Intramuscular: 0.18 L/kg</td><td style=\"padding: 5px 7px; border: 1px solid black;\">Racemate: 5.6 hours (intravenous)<br /><br />5.3 hours (oral, intramuscular)<br /><br />4.8 hours (intranasal)</td><td style=\"padding: 5px 7px; border: 1px solid black;\">99%</td><td style=\"padding: 5px 7px; border: 1px solid black;\">Not for minor or chronic pain<br /><br />Not for pediatric patients<br /><br />Risk of potentially fatal GI bleeding or perforation; elderly patients at increased risk <br /><br />Increased risk of potentially fatal cardiovascular thrombotic events, myocardial infarction, and stroke<br /><br />Peri-operative pain in CABG surgery<br /><br />Renal toxicity risk<br /><br />Bleeding risk due to platelet function inhibition<br /><br />Not for use prior to major surgery<br /><br />Risk of hypersensitivity reactions; must have measures available to treat at first-dose administration<br /><br />Contains alcohol, do not administer via intrathecal or epidural routes<br /><br />Risk of fetal harm if used during labor and delivery<br /><br />Risk to nursing neonate if used by mother<br /><br />Risk of additive adverse events if used with other NSAIDs<br /><br />Reduce dose in patients &gt;65 years old, patients weighing &lt;50 kg, or patients with elevated serum creatinine. Do not exceed total daily dose of 60 mg injectable ketorolac<br /><br />Do not exceed 5 days (combined duration, any route)</td><td style=\"padding: 5px 7px; border: 1px solid black;\">History of allergic reaction to ketorolac, aspirin, or any other NSAID<br /><br />Active peptic ulcer disease <br /><br />Recent GI bleeding or perforation<br /><br />History of GI bleeding or peptic ulcer disease<br /><br />Peri-operative pain in CABG surgery<br /><br />Advanced renal impairment<br /><br />Patients at risk of renal failure resulting from volume depletion<br /><br />Cerebrovascular bleeding (suspected or confirmed)<br /><br />Hemorrhagic diathesis<br /><br />Incomplete hemostasis<br /><br />Patients with high risk of bleeding<br /><br />Prior to any major surgery<br /><br />Intrathecal or epidural administration<br /><br />During labor and delivery<br /><br />Nursing mothers<br /><br />Concomitant use with aspirin or other NSAIDs<br /><br />Concomitant use with probenecid or pentoxifylline</td></tr><tr><td style=\"padding: 5px 7px; border: 1px solid black;\">Ibuprofen (Caldolor)</td><td style=\"padding: 5px 7px; border: 1px solid black;\">Not available</td><td style=\"padding: 5px 7px; border: 1px solid black;\">2.4 hours</td><td style=\"padding: 5px 7px; border: 1px solid black;\">&gt;99%</td><td style=\"padding: 5px 7px; border: 1px solid black;\">Increased risk of potentially fatal cardiovascular thrombotic events, myocardial infarction, and stroke; do not use for CABG surgery peri-operative pain<br /><br />Risk of potentially fatal GI bleeding, ulceration, or perforation; elderly patients at increased risk</td><td style=\"padding: 5px 7px; border: 1px solid black;\">Known hypersensitivity to ibuprofen<br /><br />History of allergic reactions, asthma, or urticaria with aspirin or any other NSAID<br /><br />Peri-operative pain in CABG surgery</td></tr><tr><td style=\"padding: 5px 7px; border: 1px solid black;\">Acetaminophen(Ofirmev)</td><td style=\"padding: 5px 7px; border: 1px solid black;\">Intravenous: 0.8 L/kg</td><td style=\"padding: 5px 7px; border: 1px solid black;\">2.4 hours</td><td style=\"padding: 5px 7px; border: 1px solid black;\">10 to 25%</td><td style=\"padding: 5px 7px; border: 1px solid black;\">Risk of medication errors and hepatotoxicity. Dosing errors could lead to accidental death and overdose. <br /><br />Risk of acute liver failure, liver transplant, or death</td><td style=\"padding: 5px 7px; border: 1px solid black;\">Known hypersensitivity to acetaminophen or excipients<br /><br />Severe hepatic impairment or active liver disease</td></tr></tbody></table>" ],
  "availableProduct" : [ {
    "NDC" : "47781-0585-68",
    "RXCUI" : "1665459",
    "textDescription" : "Ketorolac injection, Alvogen, 30 mg/mL, 2 mL vial, 25 count, NDC 47781-0585-68"
  }, {
    "NDC" : "70860-0701-03",
    "RXCUI" : "1665461",
    "textDescription" : "Ketorolac injection, Athenex, 30 mg/mL, 1 mL vial, 25 count, NDC 70860-0701-03"
  }, {
    "NDC" : "70860-0701-04",
    "RXCUI" : "1665459",
    "textDescription" : "Ketorolac injection, Athenex, 30 mg/mL, 2 mL vial, 25 count, NDC 70860-0701-04"
  }, {
    "NDC" : "63323-0161-01",
    "RXCUI" : "860092",
    "textDescription" : "Ketorolac injection, Fresenius Kabi, 15 mg/mL, 1 mL vial, 25 count, NDC 63323-0161-01"
  }, {
    "NDC" : "76045-0104-10",
    "RXCUI" : "860114",
    "textDescription" : "Ketorolac injection, Fresenius Kabi, 30 mg/mL, 1 mL prefilled syringe, 24 count, NDC 76045-0104-10"
  }, {
    "NDC" : "76045-0105-20",
    "RXCUI" : "860115",
    "textDescription" : "Ketorolac injection, Fresenius Kabi, 30 mg/mL, 2 mL for intramuscular use prefilled syringe, 24 count, NDC 76045-0105-20"
  }, {
    "NDC" : "63323-0162-02",
    "RXCUI" : "1665459",
    "textDescription" : "Ketorolac injection, Fresenius Kabi, 30 mg/mL, 2 mL for intramuscular use vial, 25 count, NDC 63323-0162-02"
  }, {
    "NDC" : "00409-3796-01",
    "RXCUI" : "1665459",
    "textDescription" : "Ketorolac injection, Pfizer, 30 mg/mL, 2 mL for intramuscular use vial, 10 count, NDC 00409-3796-01"
  }, {
    "NDC" : "69543-0386-25",
    "RXCUI" : "1665461",
    "textDescription" : "Ketorolac injection, Virtus, 30 mg/mL, 1 mL vial, 25 count, NDC 69543-0386-25"
  } ],
  "lastRevisedDate" : "17-May-2018",
  "patientCareImplications" : [ "Ketorolac is a nonsteroidal anti-inflammatory drug labeled for use in adults with moderate to severe acute pain who require short-term analgesia at the opioid level, typically following surgery.[13]  Ketorolac can be used alone, or in combination with opioid analgesics. Ketorolac is useful in situations where opioids are contraindicated or to reduce opioid dosage requirements when used in combination with opioids. Total duration of ketorolac given intravenous, intramuscular, or orally should not exceed 5 days due to the increased frequency and severity of adverse reactions. Ketorolac, given intramuscularly, is used off-label for the management of migraine.[14-15] " ],
  "reference" : [ null, "Alvogen (personal communication). April 7, and May 17, 2018. ", "Amphastar (personal communications). October 4, 2016; January 9, August 29, and September 11, 2017, May 14, 2018.", "Athenex (personal communications). February 20, March 8 and 12, April 4, and May 14, 2018. ", "BD Rx (personal communications). November 11, 2015; and February 4, 2016.", "Fresenius Kabi (personal communications).  February 2, 11, 18, and 24, March 11, 18, and 31, May 6 and 20, June 30, July 6, August 6, September 10, October 8, November 4, December 11, 2015; January 20, February 5 and 18, March 7, May 13 and 23, June 8 and 30, July 29, September 6, October 4 and 27, 2016; January 28, February 20, March 21, June 2 and 20, July 7 and 28, August 24, September 21, November 10, 17, and 30, December 15, 2017; January 12, February 5 and 15, March 2, 9, 20, and 23, April 6 and 27, and May 3 and 10, 2018.", "Pfizer (personal communications and website).  February 10 and 24, March 2, 13, and 20, April 1 and 7, May 11 and 22, July 2 and 27, September 15, October 12, November 12, December 11, 2015; January 26, February 5, 22, and 25, March 7, April 28, May 20, June 16 and 23, July 7, August 2, September 6, October 4, November 6, 2016; January 30, February 23, March 24, June 2, 5, and 23, July 7, 14, and 28, August 28, September 29, October 11, November 15, 20, and 28, December 1 and 18, 2017;  January 12, February 2, 16 and 23, March 5, 9, and 23, April 2, and May 1 and 11, 2018.", "Sagent (personal communications). February 9, 19, and 26, March 12, 20, and 27, April 2, May 7 and 21, July 2 and 30, September 10, October 8, November 5, December 10, 2015; January 21, February 4 and 18, March 7, April 28, May 19 and 26, June 16, July 7 and 29, September 6, October 4, November 3, 2016; January 27, February 23, March 23, June 1 and 22, July 7 and 28, August 24, September 28, November 9, 16, 22, and 30, December 14, 2017; January 11, February 1 and 22, March 1, 22, and 29, and May 3 and 10, 2018.", "West-Ward (personal communications).  January 29, February 18, March 11, April 2, and May 6, June 24, July 29, and September 1, 2015; January 27, March 29, 2016; and May 2 and 10, 2018.", "Ben Venue (personal communications).  August 5, 2014.", "Virtus. (personal communications). February 20, April 4, and May 15, 2018. ", "Wockhardt (personal communications).  December 9, 2013.", "Egalet Corporation (personal communications). April 1, 2015.", "Hospira. Ketorolac tromethamine injection solution [product information]. Lake Forest, IL: Hospira 2014.", "Anon, editor. Drugdex System. Micromedex 2.0 [internet database]. Greenwood Village, CO: Truven Health Analytics; 2015.", "Wickersham RM, Novak KK, managing eds., editors. Drug Facts and Comparisons (Facts & Comparisons eAnswers). St. Louis, MO: Wolters Kluwer Health, Inc.; 2015.", "Cumberland Pharmaceuticals Inc. Caldolor (ibuprofen) Injection, for intravenous use [product information]. Nashville, TN: Cumberland Pharmaceuticals Inc.; 2014.", "Hospira. Dyloject (diclofenac sodium) Injection [product information]. Lake Forest, IL: Hospira 2014.", "Cadence Pharmaceuticals. Ofirmev (acetaminophen) Injection [product information]. San Diego, CA: Cadence Pharmaceuticals, Inc.; 2010.", "Regency Therapeutics. Sprix (ketorolac tromethamine) nasal spray [product information]. Shirley, NY: American Regent 2014." ],
  "resupplyEstimateNote" : [ "Alvogen has 15 mg/mL 1 mL vials and 30 mg/mL 1 mL vials on back order with unknown release dates.1", "Amphastar has ketorolac 30 mg/mL 1 mL vials on back order and the company cannot estimate a release date.[2] ", "Fresenius Kabi has ketorolac 30 mg/mL 1 mL vials on back order and the company estimates a release date of late-May 2018.[5] ", "Pfizer has ketorolac 15 mg/mL 1 mL vials and 30 mg/mL 1 mL vials on back order and the company estimates a release date in May 2018. The 30 mg/mL 1 mL Carpuject syringes, 30 mg/mL 2 mL Carpuject syringes for intramuscular injection, and 30 mg/mL 1 mL iSecure syringes are on back order and the company estimates a release date of 2019.[6] ", "Sagent has all ketorolac products on back order. The company estimates release dates of July 2018 for the 30 mg/mL 2 mL vials for intramuscular injection, May 2018 for the 15 mg/mL 1 mL vials, and June 2018 for the 30 mg/mL 1 mL vials.[7] ", "West-Ward has ketorolac 15 mg/mL 1 mL vials, 30 mg/mL 1 mL vials, and 30 mg/mL 2 mL vials for intramuscular injection on allocation.[8] " ],
  "safetyNote" : [ "Dosage recommendations and administration times vary significantly between alternative agents. Patient harm can occur if these agents are used erroneously. Use extra caution when switching to alternative agents.[13,16-18] " ],
  "searchString" : "ketorolac injection",
  "shortageAuthor" : [ "Jane Chandramouli" ],
  "shortageCreateDate" : "10-Jul-2015",
  "shortageReason" : [ "Alvogen has ketorolac injection available in 25 count sizes.[1] ", "Amphastar did not provide a reason for the shortage.[2] ", "Athenex has ketorolac injection available.[3] ", "BD RX is now part of Fresenius Kabi.[4] ", "Fresenius Kabi did not provide a reason for the shortage.[5] ", "Pfizer has ketorolac injection on back order due to manufacturing delays.[6] ", "Sagent states the reason for the shortage is manufacturing delay.[7] ", "West-Ward did not provide a reason for the shortage.[8] ", "Ben Venue closed its plant in Bedford, Ohio in July 2014.[9] ", "Virtus has ketorolac injection available.[10] ", "FDA imposed an import ban in mid-2013 on several Wockhardt products including ketorolac.[11] ", "Sprix Nasal Spray is not affected by this shortage.[12] " ],
  "shortageStatus" : "Active",
  "shortageTitle" : "Ketorolac Injection",
  "shortageVersion" : "55",
  "updateHistory" : "Updated May 17, 2018 by Anthony Trovato, Pharmacy Resident. Created August 6, 2015 by Jane Chandramouli, PharmD, Drug Information Specialist. Copyright 2018, Drug Information Service, University of Utah, Salt Lake City, UT.",
  "updatedAt" : 1526583269489
}

```
## Sample API calls
---
**To get all active shortages:**

/drugShortages.json?print=pretty&orderBy="/latest/shortageStatus"&equalTo="Active"&auth={apiKey}

**To get shortages since a date (Linux Epoch format in milliseconds):**

/drugShortages.json?auth={apiKey}&print=pretty&orderBy="latest/updatedAt"&startAt=1556668800000

[Full API usage documentation](https://firebase.google.com/docs/reference/rest/database)


