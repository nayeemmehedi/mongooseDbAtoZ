#### mongoose delete 

                                      module.exports.productDelete = async (req, res, next) => {
                                        try {
                                          const { id } = req.params;

                                          const result = await Product.deleteOne({ _id: id });

                                          res.status(200).json({
                                            status: "Successful",
                                            message: "delete data Successfully",
                                            result,
                                          });
                                        } catch (error) {
                                          res.status(400).json({
                                            status: "faild",
                                            message: error.message,
                                          });
                                        }
                                      };

                                      module.exports.productDeleteMany = async (req, res, next) => {
                                        // {
                                        //     ids : ["ddd","dddd"]
                                        // }

                                        try {
                                          const result = await Product.deleteMany({ _id: req.body.ids });

                                          if (!result.deletedCount) {
                                            res.status(400).json({
                                              status: "faild",
                                              message: "No data there",
                                            });
                                          } else {
                                            res.status(200).json({
                                              status: "Successful",
                                              message: "delete data Successfully",
                                              result,
                                            });
                                          }
                                        } catch (error) {
                                          res.status(400).json({
                                            status: "faild",
                                            message: error.message,
                                          });
                                        }
                                      };
