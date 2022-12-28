       #### router basic : 
       
                  const express = require("express")
                  const { productControllerGet,productControllerPost, productControllerGetbyId, productControllerPostMany, productControllerPatchbyId } =                                  require("../controller/product.controller")

                  const productRoute = express.Router()

                  productRoute.route("/")
                                  .get(productControllerGet)
                                  .post(productControllerPost)



                  productRoute.route("/many")
                                 .post(productControllerPostMany)




                  productRoute.route("/:id")
                                  .get(productControllerGetbyId)
                                  .patch(productControllerPatchbyId)


                  module.exports = productRoute
