String as 

# basic / Array 
This block merges the inputs into an array. If one of the input is itself an array is will be flatten into the main array
* Inputs
** item1
** item2
** item3
** item4
** item5
* Outputs
** item1
** item2
** item3
** item4
** item5


# controls / CheckPhoneNumber 
This check the provided phone number according to the country. It returns the reformatted phone number and the validation status
* Inputs
** phoneNumber
** countryISO2
** Uri
* Outputs
** phoneNumber
** countryISO2
** Uri


# controls / checkRequiredFields* 

* Inputs
** node
* Outputs
** node


# controls / isInDictionnary* 

* Inputs
** value
* Outputs
** value


# controls / isDate* 

* Inputs
** value
* Outputs
** value


# controls / isNumber* 

* Inputs
** value
* Outputs
** value


# controls / Schematron validation* 

* Inputs
** doc
* Outputs
** doc


# controls / XMLValidate 

* Inputs
** node
* Outputs
** node


# controls / JsonValidate 

* Inputs
** node
** schema
* Outputs
** node
** schema


# cts / Doc 

* Inputs
** uri
* Outputs
** uri


# cts / ExpertQueryBuilder 

* Inputs
** v0
** v1
* Outputs
** v0
** v1


# cts / jsonPropertyValueQuery 

* Inputs
** property
** value
* Outputs
** property
** value


# cts / collectionQuery 

* Inputs
** collectionName
* Outputs
** collectionName


# cts / search 

* Inputs
** query
* Outputs
** query


# cts / orQuery 

* Inputs
** query1
** query2
** query3
** query4
* Outputs
** query1
** query2
** query3
** query4


# cts / andQuery 

* Inputs
** query1
** query2
** query3
** query4
* Outputs
** query1
** query2
** query3
** query4


# date / FormatDateTimeAuto 
This block formats input datetime to ISO format using predefined formats (momentjs)
* Inputs
** inputDateTime
* Outputs
** inputDateTime


# date / FormatDateAuto 
This blocks formats the input date to ISO format using MM-DD-YYYY, YYYY-MM-DD, DD/MM/YYYY
* Inputs
** inputDate
* Outputs
** inputDate


# date / FormatDate 
This blocks formats the input date to ISO format using the provided format
* Inputs
** inputDate
* Outputs
** inputDate


# dhf / declarativeMapper 
This block applies DHF 5.1 mapping to the input node
* Inputs
** node
* Outputs
** node


# feature / selectCase 
This block returns one of the inputX value depending on the value2Test input. The selection of inputX is done based on the block configuration (double click)
* Inputs
** value2Test
** input0
** input1
** input2
* Outputs
** value2Test
** input0
** input1
** input2


# feature / DistinctValues 
This block returns the distinct values of a property from the input (can be array or sequence with reasonable size
* Inputs
** array
* Outputs
** array


# feature / Lookup 

* Inputs
** query
** var1
** var2
* Outputs
** query
** var1
** var2


# fn / head 

* Inputs
** nodes
* Outputs
** nodes


# fn / doc 

* Inputs
** uri
* Outputs
** uri


# fn / collection 

* Inputs
** collectionName
* Outputs
** collectionName


# fn / baseUri 

* Inputs
** node
* Outputs
** node


# fn / count 

* Inputs
** list
* Outputs
** list


# geo / GeoReproject 
This block converts geo coordinates from source coordinate system to the target one.
* Inputs
** srcCoordinateSystem
** targetCoordinateSystem
** strWKT
* Outputs
** srcCoordinateSystem
** targetCoordinateSystem
** strWKT


# provenance / PROV-O structure 
This block generates provo triples based on the provided inputs
* Inputs
** uri
** DerivedFrom1
** DerivedFrom2
** DerivedFrom3
** GeneratedBy
** createdOn
* Outputs
** uri
** DerivedFrom1
** DerivedFrom2
** DerivedFrom3
** GeneratedBy
** createdOn


# string / String join 
This block joins the input array of strings using the provided separator
* Inputs
** string*
* Outputs
** string*


# string / Map values 
This block maps an input value to another using the configuration of the block (double click)
* Inputs
** value
* Outputs
** value


# string / Split 
This block splits the input string using the provided char.
* Inputs
** string
* Outputs
** string


# string / UpperCase 

* Inputs
** string
* Outputs
** string


# string / Highlight 
This block applies MarkLogic highlight function to the input string
* Inputs
** string
** query
** highlightKeyword
* Outputs
** string
** query
** highlightKeyword


# string / LowerCase 

* Inputs
** STRING
* Outputs
** STRING


# string / EntityEnrichment 
This block performs entity enrichment on the input string based on a dictionary
* Inputs
** string
** dictionary
* Outputs
** string
** dictionary


# string / uuid 
This block generates an UUID string
* Inputs

* Outputs



# transform / ApplyXSLT 
This block applies the input XSL to the input node. XSL can be a string or the URI in module DB of the XSL
* Inputs
** node
** xslStr
** xslPath
* Outputs
** node
** xslStr
** xslPath


# transform / Add property 

* Inputs
** doc
** value
* Outputs
** doc
** value


# triples / CreateTriple 
This block creates a triple using the provided subject, predicate, object
* Inputs
** subject
** object
* Outputs
** subject
** object