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
