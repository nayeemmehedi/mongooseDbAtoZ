### Mongoose Schema

                                let productSchema = mongoose.Schema(
                                  {
                                    //name
                                    name : {
                                    
                                      type: String,
                                      
                                      required: [true, "Please provide a name .."],
                                      
                                      trim: true,
                                      
                                      unique: true,
                                      
                                      minLength: [3, "Name must be 3 charecter"],
                                      
                                      maxLength: [10, "Name must be 10 charecter less"],
                                      
                                    },
                                    //description
                                   description: {
                                    
                                      type: String,
                                      
                                      required: true,
                                      
                                    },
                                    
                                    //price
                                    
                                   price: {
                                    
                                      type: Number,
                                      
                                      required: true,
                                      
                                      min: [0, "price can't be negative"],
                                      
                                    },
                                    
                                    //unit
                                    
                                   unit  : {
                                      type: String,
                                      
                                      required: true,
                                      
                                      // enum :["kg","litre","pcs"]
                                      
                                      enum: {
                                      
                                        values: ["kg", "litre", "pcs"],
                                        message: "Unit must be kg,litre,pcs",
                                        
                                      },
                                    },
                                    
                                    
                                    // quantity
                                    
                                   quantity: {
                                    
                                      type: Number,
                                      
                                      required: true,
                                      
                                      min: 0,
                                      
                                      // validate: {
                                      //   validator: (value) => {
                                      //     const isInt = Number.isInteger(value);
                                      //     if (isInt) {
                                      //       return true;
                                      //     } else {
                                      //       return false;
                                      //     }
                                      //   },
                                      // },
                                      
                                      message: "Quantity must be an integer",
                                    },
                                    
                                    // status
                                    
                                    status: {
                                    
                                      type: String,
                                      
                                      required: true,
                                      
                                      enum: {
                                      
                                        values: ["in-stock", "out-of-stock", "discontinued"],
                                        
                                        message: "in-stock,out-of-stock,discontinued",
                                      },
                                    },

                                    /**
                                   * ambet and referencve 
                                   * 
                                   * 1.ambet - hardcord r maddhme rakha
                                   *      dhoren pnr name nayem ata r change kora jbe na

                                     2. referenc - onnon jaiga name change hyle eikhne o change hbe
                                  */

                                    // reference example
                                    // supplier: {
                                    //   type: mongoose.Schema.Types.ObjectId,
                                    //   ref: "Supplier",
                                    // },

                                    // //ambet object
                                    // categories: [
                                    //   {
                                    //     name: {
                                    //       type: String,
                                    //       required: true,
                                    //     },
                                    //     _id: mongoose.Schema.Types.ObjectId,
                                    //   },
                                    // ],
                                    // createdAt :{
                                    //   type :Date,
                                    //   default:Date.now,

                                    // },
                                    // updatedAt : {
                                    //   type :Date,
                                    //   default:Date.now
                                    // }
                                  },
                                  {
                                   #### timestamps: true,
                                  }
                                );

### middleware mongoose :
                    
pre :
                               productSchema.pre('save', function (next) {
 
                                    if (this.quantity == 0) {
                                      this.status = "out-of-stock";
                                    }
                                    next();
                                  });
                                  
                                  
post :             
          
                                  productSchema.post("save", function (doc, next) {
                                  
                                    console.log("before");
                                    next();
                                  });

model : 

                            const Product = mongoose.model("Product", productSchema);
                            
