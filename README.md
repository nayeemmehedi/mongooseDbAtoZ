#### advance query 

                      
                                                                            module.exports.productGetMore = async (req, res) => {
                                                        try {
                                                          const mainQuery = { ...req.query };

                                                          const extraValue = ["limit", "page", "sort"];

                                                          extraValue.map((value) => delete mainQuery[value]);

                                                          const quearis = {};

                                                          if (req.query.sort) {
                                                            quearis.data = req.query.sort;
                                                          } else {
                                                            // const data = await Product.find(mainQuery)
                                                            quearis.data = req.query.sort;
                                                          }

                                                          if (req.query.fields) {
                                                            quearis.fields = req.query.fields.split(",").join(" ");
                                                          }

                                                          //http://localhost:3000/api/v1/product/more?price[gt]=100
                                                          // const value = { price : { gt :50}}

                                                          let filterString = JSON.stringify(mainQuery);

                                                          filterString = filterString.replace(
                                                            /\b(gt|gte|lt|lte)\b/g,
                                                            (match) => `$${match}`
                                                          );

                                                          let gotFilter = JSON.parse(filterString);
                                                          console.log(gotFilter);

                                                          //pegination
                                                          /**
                                                          http://localhost:3000/api/v1/product/more?page=2&limit=2
                                                           * 
                                                           * page 1 -> 1-10
                                                           * page 2 -> 11-20
                                                           * page 3 -> 21-30
                                                           * thle 3 page pete hyle ager 20 ta skip krte hbe
                                                           * page 3 - 1 * limit 10
                                                          */

                                                          if (req.query.page) {
                                                            const { page = 1, limit = 10 } = req.query;

                                                            const skip = (page - 1) * +limit;

                                                            quearis.skip = skip;
                                                            quearis.limit = +limit;
                                                          }

                                                          const data = await Product.find(gotFilter)
                                                            .skip(quearis.skip)
                                                            .limit(quearis.limit)
                                                            .select(quearis.fields)
                                                            .sort(quearis.data);

                                                            //total product 
                                                          const totalProduct = await Product.countDocuments(gotFilter);
                                                          // http://localhost:3000/api/v1/product/more?page=2&limit=3
                                                          const pageCount = Math.ceil(totalProduct/quearis.limit)

                                                          res.status(200).json({
                                                            status: "success",
                                                            totalProduct,
                                                            pageCount,
                                                            data: data,
                                                          });
                                                        } catch (error) {
                                                          res.status(400).json({
                                                            status: "faild",
                                                            message: error.message,
                                                          });
                                                        }
                                                      };
