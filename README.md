#### update mongoose

                 module.exports.productUpdate = async (req, res, next) => {
                  try {
                    const { id } = req.params;
                    //jdi amra name : null dei kono verifation krbe na ..updateone e.

                    const result = await Product.updateOne(
                      { _id: id },
                      { $set: req.body },
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

