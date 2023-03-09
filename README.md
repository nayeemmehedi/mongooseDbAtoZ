### Schema 

https://www.geeksforgeeks.org/mongoose-schematype/

1.  `Type` : Specifies the data type of the field. Mongoose supports various data types, such as String, Number, Date, Boolean, etc.

         type : String

2. `Required` : Specifies whether the field is required or not. If this property is set to true, then the field must have a value before the document can be saved.

     
          required : true         
          required : [true,"This field required"]
          

3. `Default` : Specifies the default value of the field. If the field is not provided with a value, then the default value is used.

4. `Unique` : Specifies whether the field value should be unique across all documents in the collection. If this property is set to true, then Mongoose will create a unique index on the field.

       unique : true

5. `Validate` : Specifies a custom validation function for the field. The validation function takes a value as input and returns true if the value is valid, or false otherwise.

         validate : {
                validator : (value)=>{
                
                    value > 5 ?  true : false
                    
                    }
                    
                    message :"something worong"
                
                
                
                }

6. `Enum` : Specifies an array of allowed values for the field. If this property is set, then the field value must be one of the allowed values.


       enum : ["kg","litter"]
       
       enum : {
          value :  ["kg","litter"],
          message :"kg/litter must be needed"
       
       }
       
       

7. `Min/Max` : Specifies the minimum or maximum value for a number field.

          min : [30, must be less then 30]
          
 8. MinLength/MaxLength : Specifies the minimum or maximum value for a string field.
 
         minLength : [30, must be less then 30 charector]

9. `Trim` : Specifies whether Mongoose should trim whitespace from the beginning and end of a string field.

        trim : true
        
        
    age piche space thkle kete dbe

10. `Lowercase/Uppercase`  : Specifies whether Mongoose should convert the string field to lowercase or uppercase.

12. `Ref`: Specifies a reference to another model. This property is used for defining relationships between models in Mongoose.

            supplier : {
            
               type : mongoose.Schema.Types.ObjectId , 
               ref : "Supplier"
            
            }


13 . `timeStamps` : true
