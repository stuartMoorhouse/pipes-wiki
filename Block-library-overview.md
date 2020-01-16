
# basic / Array 
This block merges the inputs into an array. If one of the input is itself an array is will be flatten into the main array
* **Inputs**
  * item1  
  * item2  
  * item3  
  * item4  
  * item5  
* **Block settings ("Widgets")**
  * None
* **Outputs**
  * array  


# controls / CheckPhoneNumber 
This check the provided phone number according to the country. It returns the reformatted phone number and the validation status
* **Inputs**
  * phoneNumber  
  * countryISO2  
  * Uri  
* **Block settings ("Widgets")**
  * outputFormat  
  * defaultCountry  
  * Output if invalid ?  
* **Outputs**
  * phoneNumber  
  * countryCode  
  * numberType  
  * qualityResult  


# controls / checkRequiredFields* 

* **Inputs**
  * node  
* **Block settings ("Widgets")**
  * None
* **Outputs**
  * status  


# controls / isInDictionnary* 

* **Inputs**
  * value  
* **Block settings ("Widgets")**
  * None
* **Outputs**
  * status  


# controls / isDate* 

* **Inputs**
  * value  
* **Block settings ("Widgets")**
  * None
* **Outputs**
  * status  


# controls / isNumber* 

* **Inputs**
  * value  
* **Block settings ("Widgets")**
  * None
* **Outputs**
  * status  


# controls / Schematron validation* 

* **Inputs**
  * doc  
* **Block settings ("Widgets")**
  * None
* **Outputs**
  * SVRL  


# controls / XMLValidate 

* **Inputs**
  * node  
* **Block settings ("Widgets")**
  * None
* **Outputs**
  * results  


# controls / JsonValidate 

* **Inputs**
  * node  
  * schema  
* **Block settings ("Widgets")**
  * None
* **Outputs**
  * results  


# cts / Doc 

* **Inputs**
  * uri  
* **Block settings ("Widgets")**
  * None
* **Outputs**
  * doc  


# cts / ExpertQueryBuilder 

* **Inputs**
  * v0  
  * v1  
* **Block settings ("Widgets")**
  * nbInputs  
* **Outputs**
  * ctsQuery  


# cts / jsonPropertyValueQuery 

* **Inputs**
  * property  
  * value  
* **Block settings ("Widgets")**
  * case  
  * diacritic  
  * punctuation  
  * whitespace  
  * stemming  
  * wildcard  
  * exact  
* **Outputs**
  * query  


# cts / collectionQuery 

* **Inputs**
  * collectionName  
* **Block settings ("Widgets")**
  * None
* **Outputs**
  * query  


# cts / search 

* **Inputs**
  * query  
* **Block settings ("Widgets")**
  * None
* **Outputs**
  * results  


# cts / orQuery 

* **Inputs**
  * query1  
  * query2  
  * query3  
  * query4  
* **Block settings ("Widgets")**
  * None
* **Outputs**
  * query  


# cts / andQuery 

* **Inputs**
  * query1  
  * query2  
  * query3  
  * query4  
* **Block settings ("Widgets")**
  * None
* **Outputs**
  * query  


# date / FormatDateTimeAuto 
This block formats input datetime to ISO format using predefined formats (momentjs)
* **Inputs**
  * inputDateTime  
* **Block settings ("Widgets")**
  * None
* **Outputs**
  * IsoDateTime  


# date / FormatDateAuto 
This blocks formats the input date to ISO format using MM-DD-YYYY, YYYY-MM-DD, DD/MM/YYYY
* **Inputs**
  * inputDate  
* **Block settings ("Widgets")**
  * None
* **Outputs**
  * IsoDate  


# date / FormatDate 
This blocks formats the input date to ISO format using the provided format
* **Inputs**
  * inputDate  
* **Block settings ("Widgets")**
  * format  
* **Outputs**
  * IsoDate  


# dhf / declarativeMapper 
This block applies DHF 5.1 mapping to the input node
* **Inputs**
  * node  
* **Block settings ("Widgets")**
  * MappingName  
  * MappingVersion  
  * WithInstanceRoot  
* **Outputs**
  * mappedNode  


# feature / selectCase 
This block returns one of the inputX value depending on the value2Test input. The selection of inputX is done based on the block configuration (double click)
* **Inputs**
  * value2Test  
  * input0  
  * input1  
  * input2  
* **Block settings ("Widgets")**
  * nbInputs  
* **Outputs**
  * value  


# feature / DistinctValues 
This block returns the distinct values of a property from the input (can be array or sequence with reasonable size
* **Inputs**
  * array  
* **Block settings ("Widgets")**
  * xpath  
* **Outputs**
  * distinctValues  


# feature / Lookup 

* **Inputs**
  * query  
  * var1  
  * var2  
* **Block settings ("Widgets")**
  * query  
  * valuePath  
* **Outputs**
  * value  


# fn / head 

* **Inputs**
  * nodes  
* **Block settings ("Widgets")**
  * None
* **Outputs**
  * node  


# fn / doc 

* **Inputs**
  * uri  
* **Block settings ("Widgets")**
  * None
* **Outputs**
  * doc  


# fn / collection 

* **Inputs**
  * collectionName  
* **Block settings ("Widgets")**
  * None
* **Outputs**
  * docs  


# fn / baseUri 

* **Inputs**
  * node  
* **Block settings ("Widgets")**
  * None
* **Outputs**
  * uri  


# fn / count 

* **Inputs**
  * list  
* **Block settings ("Widgets")**
  * None
* **Outputs**
  * nbItems  


# geo / GeoReproject 
This block converts geo coordinates from source coordinate system to the target one.
* **Inputs**
  * srcCoordinateSystem : Source coordinate system
  * targetCoordinateSystem : Target coordinate system
  * strWKT : Geo shape
* **Block settings ("Widgets")**
  * None
* **Outputs**
  * strWKT : Converted geo shape


# provenance / PROV-O structure 
This block generates provo triples based on the provided inputs
* **Inputs**
  * uri : URI of the source
  * DerivedFrom1 : Optional derived from URI
  * DerivedFrom2 : Optional derived from URI
  * DerivedFrom3 : Optional derived from URI
  * GeneratedBy : Optional generated by URI
  * createdOn : Optional date
* **Block settings ("Widgets")**
  * None
* **Outputs**
  * PROV-O  


# string / String join 
This block joins the input array of strings using the provided separator
* **Inputs**
  * string*  
* **Block settings ("Widgets")**
  * None
* **Outputs**
  * joinedString  


# string / Map values 
This block maps an input value to another using the configuration of the block (double click)
* **Inputs**
  * value  
* **Block settings ("Widgets")**
  * castOutput  
* **Outputs**
  * mappedValue  


# string / Split 
This block splits the input string using the provided char.
* **Inputs**
  * string  
* **Block settings ("Widgets")**
  * splitChar  
* **Outputs**
  * v1  
  * v2  
  * v3  
  * array  


# string / UpperCase 

* **Inputs**
  * string  
* **Block settings ("Widgets")**
  * None
* **Outputs**
  * STRING  


# string / Highlight 
This block applies MarkLogic highlight function to the input string
* **Inputs**
  * string  
  * query  
  * highlightKeyword  
* **Block settings ("Widgets")**
  * None
* **Outputs**
  * enrichedString  


# string / LowerCase 

* **Inputs**
  * STRING  
* **Block settings ("Widgets")**
  * None
* **Outputs**
  * string  


# string / EntityEnrichment 
This block performs entity enrichment on the input string based on a dictionary
* **Inputs**
  * string : String to enrich
  * dictionary : URI of a SKOS dictionary
* **Block settings ("Widgets")**
  * None
* **Outputs**
  * enrichedString : Enriched string


# string / uuid 
This block generates an UUID string
* **Inputs**

* **Block settings ("Widgets")**
  * prefix : This value can be added as a prefix to the UUID
* **Outputs**
  * uuid  


# transform / ApplyXSLT 
This block applies the input XSL to the input node. XSL can be a string or the URI in module DB of the XSL
* **Inputs**
  * node  
  * xslStr  
  * xslPath  
* **Block settings ("Widgets")**
  * None
* **Outputs**
  * doc  


# transform / Add property 

* **Inputs**
  * doc  
  * value  
* **Block settings ("Widgets")**
  * None
* **Outputs**
  * doc  


# triples / CreateTriple 
This block creates a triple using the provided subject, predicate, object
* **Inputs**
  * subject  
  * object  
* **Block settings ("Widgets")**
  * subjectIsIRI  
  * predicate  
  * objectIsIRI  
* **Outputs**
  * triple  