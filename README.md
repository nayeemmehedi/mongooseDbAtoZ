### get doc mongoose


//get doc with code

//3 vbe get kiora jay find ,findone,find by id


                              app.get("/api/v1/product",async (req, res) => {

                                try {

                                  // rules 1 - sob value 
                                  const data = await Product.find({}) 

                                  // rule 2  - or opearator 

                                  // const data = await Product.find({$or : [
                                  //   {_id :"63949e3a810775f54b51424e"},
                                  //   { name :"dal"},

                                  // ]}) 

                                  // rules 3 -
                                  // const data = await Product.find({
                                  //   price : { $eq :"out-of-stock"}
                                  // }) 

                                //  rules 4 - 
                                //   const data = await Product.find({
                                //     price : { $lt :90}
                                //   }) 

                                //  rules 5 - 
                                  // const data = await Product.find({
                                  //   name : { $in : ["chal","dal"]}
                                  // }) 

                                  //  rules 6 - only j j property lgbe segulo
                                  // const data = await Product.find({},"name price -_id") 

                                  //  rules 7
                                  // const data = await Product.find({}).sort({price : -1})

                                  // rules 8
                                  // const data = await Product.find({}).limit(2)

                                  // rules 9 
                                  // const data = await Product.find({}).limit(2)

                                  //  rules 10 
                                  // const data = await (await Product.where("name").equals("chal").where("quantity").gt(100))

                                  // rules 11 
                                  // const data = await Product.findById("6396b8f37a6115ab8068f734")




                                  res.status(200).json({
                                    status : "success",
                                    data
                                  })

                                } catch (error) {

                                  res.status(400).json({
                                    status: "faild",
                                    message: error.message,
                                  });


                                }

                              });
