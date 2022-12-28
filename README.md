# create post mongoose

                    app.post("/api/v1/product", async (req, res, next) => {
                      try {
                        /**
                         * mongoose e 2 way t post kora jay
                         * 1.save
                         * 2.create
                         */

                        //save
                        /**
                         *   const value = new Product(req.body);
                             const result = await value.save();

                        */

                        //create
                        const result = await Product.create(req.body);

                        res.status(200).json({
                          status: "Successful",
                          message: "posted data Successfully",
                          data: result,
                        });
                      } catch (error) {
                        res.status(200).json({
                          status: "faild",
                          message: error.message,
                        });
                      }
                    });
