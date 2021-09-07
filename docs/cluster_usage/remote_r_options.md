# Running R on Jupyter

Use IRKernel: https://irkernel.github.io/installation/#binary-panel

To install:

- Use conda

    `conda install -c r r-irkernel`

- Make kernel available to jupyter

    At terminal:
    ```
    R
    ```

    At the R-prompt:
    ```r
    IRkernel::installspec()
    ```
