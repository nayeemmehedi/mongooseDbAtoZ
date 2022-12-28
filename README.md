#### post many



            module.exports.productControllerPostMany =async (req, res) => {

            try {

              const result = await Product.insertMany(req.body, { runValidators: true });

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
