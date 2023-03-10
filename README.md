### :palm_tree: Schema 

 :feather:https://www.geeksforgeeks.org/mongoose-schematype/

1.  `Type` : Specifies the data type of the field. Mongoose supports various data types, such as String, Number, Date, Boolean, etc. :writing_hand:

         type : String

2. `Required` : Specifies whether the field is required or not. If this property is set to true, then the field must have a value before the document can be saved.:writing_hand:

     
          required : true         
          required : [true,"This field required"]
          

3. `Default` : Specifies the default value of the field. If the field is not provided with a value, then the default value is used. :writing_hand:

          default: 'John Doe'

4. `Unique` : Specifies whether the field value should be unique across all documents in the collection. If this property is set to true, then Mongoose will create a unique index on the field. :writing_hand:

       unique : true

5. `Validate` : Specifies a custom validation function for the field. The validation function takes a value as input and returns true if the value is valid, or false otherwise. :writing_hand:

         validate : {
                validator : (value)=>{
                
                    value > 5 ?  true : false
                    
                    }
                    
                    message :"something worong"
                
                
                
                }

6. `Enum` : Specifies an array of allowed values for the field. If this property is set, then the field value must be one of the allowed values. :writing_hand:


       enum : ["kg","litter"]
       
       enum : {
          value :  ["kg","litter"],
          message :"kg/litter must be needed"
       
       }
       
       

7. `Min/Max` : Specifies the minimum or maximum value for a number field. :writing_hand:

          min : [30, must be less then 30]
          
 8. `MinLength/MaxLength` : Specifies the minimum or maximum value for a string field. :writing_hand:
 
         minLength : [30, must be less then 30 charector]

9. `Trim` : Specifies whether Mongoose should trim whitespace from the beginning and end of a string field. :writing_hand:

        trim : true
        
        
    age piche space thkle kete dbe



10. `Ref`: Specifies a reference to another model. This property is used for defining relationships between models in Mongoose. :writing_hand:

            supplier : {
            
               type : mongoose.Schema.Types.ObjectId , 
               ref : "Supplier"
            
            }


11 . `timeStamps` : true


12 .  `Match` : 

                 match: /^[a-z0-9._%+-]+@[a-z0-9.-]+\.[a-z]{2,}$/
                 
                 match: [/^[a-z0-9._%+-]+@[a-z0-9.-]+\.[a-z]{2,}$/, 'Invalid email format']
                 


13. `Lowercase/Uppercase`  : Specifies whether Mongoose should convert the string field to lowercase or uppercase. :writing_hand:

    uppercase :duck:
    
        match: /^[A-Z]+$/
        
    lowercase :duck:
        
        match: /^[a-z]+$/
        
    email  :duck:
    
         match: /^[a-z0-9._%+-]+@[a-z0-9.-]+\.[a-z]{2,}$/
       
    both uppercase and lowercase letters :duck: ,
    
        match: /^[A-Za-z]+$/
        
        
     example :  :parrot:
     
         const userSchema = new mongoose.Schema({
           name: {
             type: String,
             required: true,
             match: /^[a-z]+$/
           },
           age: {
             type: Number,
             required: true
           },
           email: {
             type: String,
             required: true,
             match: /^[a-z0-9._%+-]+@[a-z0-9.-]+\.[a-z]{2,}$/
           }
         });

         const UserModel = mongoose.model('User', userSchema);

         module.exports = UserModel;

     
      

########################

14. uppercase check  :writing_hand:

         const productSchema = new mongoose.Schema({

           name: {
             type: String,
             required: true,
             match: /^[A-Z]+$/
           }


         });
