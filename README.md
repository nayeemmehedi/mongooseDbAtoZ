#### update many mongoose ''

                          module.exports.productUpdateMany = async (req, res, next) => {
                              try {

                                //jdi amra name : null dei kono verifation krbe na ..updateone e.
                                /**
                                 * {
                                 *  ids : [array asbe id e],
                                 * data :{
                                 * }
                                 * }
                                */

                                const result = await Product.updateMany(
                                  { _id: req.body.ids }, //array id r
                                  req.body.data,
                                  { runValidators: true }
                                );

                                res.status(200).json({
                                  status: "Successful",
                                  message: "update data Successfully",
                                  result,
                                  data: req.body,
                                });
                              } catch (error) {
                                res.status(400).json({
                                  status: "faild",
                                  message: error.message,
                                });
                              }
                            };
                            
                            
 update many different value different id :
 
                   
                     module.exports.productUpdateManyDifferentValue = async (req, res, next) => {
                     
                        try {
                        
                          // {
                          //     "ids" : [
                          //         {
                          //             "id" : "6396b8f37a6115ab8068f734",
                          //             "data": {
                          //                  "price" : 500

                          //             }

                          //         },
                          //          {
                          //             "id" : "6396b8f37a6115ab8068f733",
                          //            "data": {
                          //                  "price" : 10

                          //             }
                          //         }

                          //     ]
                          // }
                          

                          const product = [];

                          req.body.ids.forEach((singleItem) => {
                            product.push(
                              Product.updateOne(
                                {
                                  _id: singleItem.id,
                                },
                                singleItem.data
                              )
                            );
                          });

                          const result = await Promise.all(product);

                          res.status(200).json({
                            status: "Successful",
                            message: "update data Successfully",
                            result,
                            data: req.body,
                          });
                        } catch (error) {
                          res.status(400).json({
                            status: "faild",
                            message: error.message,
                          });
                        }
                      };
