### mongoose db connections

app.js
.........

                      const express = require("express");
                      const cors = require("cors");
                      const mongoose = require("mongoose");
                      const Product = require("./model/Product.model");
                      const {routerProduct,routerProduct1} = require("./routes/product.routes");



                      const app = express();
                      app.use(cors());
                      app.use(express.json());
                      app.use("/api/v1/product",routerProduct)
                      app.use("/api/v1/fileUpload",routerProduct1)


                      mongoose.set("strictQuery", true);

                      mongoose
                        .connect(process.env.DATABASE_FILE || "mongodb://localhost:27017/mongoose1st")
                        .then(() => console.log("db conntected.."));


app.listen(3000);
