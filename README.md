## product model  

          const mongoose = require("mongoose")

              const ProductSchema = new mongoose.Schema({
                  name:{
                      type : String,
                      required  : true,
                      unique : true ,
                      minLength : 2,
                      maxLength :20

                  } ,
                  description: {

                      type : String,
                      required  : true,
                      unique : true ,
                      minLength : 2,
                      maxLength :100



                  },
                  Sub_Product : [{
                      type : mongoose.Types.ObjectId,
                      ref :"sub_Product"
                  }]

              },{
                  timestamps : true
              })

              const Product = mongoose.model("Product",ProductSchema)

              module.exports = Product
              
              
              
 ## sub product model
 
         const mongoose = require("mongoose")

                const sub_ProductSchema = new mongoose.Schema({
                    name:{
                        type : String,
                        required  : true,
                        unique : true ,
                        minLength : 2,
                        maxLength :20

                    } ,

                    price : {

                        type : Number,
                        required  : true, 
                        min : 0,


                    },
                    product : {
                        type : mongoose.Types.ObjectId,
                        ref :"Product"
                    }


                },{
                    timestamps : true
                })

                const sub_Product = mongoose.model("sub_Product",sub_ProductSchema)

                module.exports = sub_Product
                
                
    ##  main work : sub product post with product id
    
                                   module.exports.sub_ProductControllerPost = async (req, res) => {
                                          try {
                                            const value = new sub_Product(req.body);

                                            const result = await value.save();


                                            const {_id, product} = result

                                            const productUpdate = await Product.updateOne({_id : product} ,{$push : {Sub_Product : _id}})

                                            res.status(200).send({
                                              status: "success",
                                              message: result,
                                            });
                                          } catch (error) {
                                            res.status(400).send({
                                              status: "failed",
                                              message: error.message,
                                            });
                                          }
                                        };
