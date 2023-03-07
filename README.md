### Schema 

`Type` : Specifies the data type of the field. Mongoose supports various data types, such as String, Number, Date, Boolean, etc.

`Required` : Specifies whether the field is required or not. If this property is set to true, then the field must have a value before the document can be saved.

`Default` : Specifies the default value of the field. If the field is not provided with a value, then the default value is used.

`Unique` : Specifies whether the field value should be unique across all documents in the collection. If this property is set to true, then Mongoose will create a unique index on the field.

`Validate` : Specifies a custom validation function for the field. The validation function takes a value as input and returns true if the value is valid, or false otherwise.

`Enum` : Specifies an array of allowed values for the field. If this property is set, then the field value must be one of the allowed values.

`Min/Max` : Specifies the minimum or maximum value for a number field.

`Trim` : Specifies whether Mongoose should trim whitespace from the beginning and end of a string field.

`Lowercase/Uppercase`  : Specifies whether Mongoose should convert the string field to lowercase or uppercase.

`Ref`: Specifies a reference to another model. This property is used for defining relationships between models in Mongoose.
