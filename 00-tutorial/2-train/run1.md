Run the data generation function `gen-iris` (see `gen_iris.py`{{open}}):

`mlrun run -f gen-iris --local`{{execute}}

> `--local` indicate we run locally (not over the cluster)

Notice the use of MLRun `with mlrun.get_or_create_ctx()` in the code: 
it wraps your code, automatically tracking the execution.

Check out the output CSV file in `artifacts/dataset.csv`{{open}}

We can also run the function using the regular `Python` command:

`python3 gen_iris.py`{{execute}}

However, when using `python` we have limited control over the execution. 

**Using MLRun execution context**

Functions can specify a `context` input or get it using `get_or_create_ctx()`,
the context allow us to read task metadata (name, uid, ..), parameters, secrets, etc.
The context also provide APIs to log outputs with `log_result()`, `log_artifact()`, `log_dataset()`, etc. and to `set_label()` 
(for tagging the run and searching/filtering runs).

<details><summary>Expand to see common context methods:</summary>

<br>

- `get_secret(key: str)` &mdash; get the value of a secret <br>
- `logger.info("started experiment..")`  &mdash; textual logs <br>
- `log_result(key: str, value)` &mdash; log simple values <br>
- `set_label(key, value)` &mdash; set a label tag for that task <br>
- `log_artifact(key, body=None, local_path=None, ...)` &mdash; log an artifacts (body or local file) <br>
- `log_dataset(key, df, ...)` &mdash; log a dataframe object <br>
- `log_model(key, ...)` &mdash; log a model object <br>

<br>

read more under [MLRun execution context](https://docs.mlrun.org/en/latest/api/mlrun.execution.html)

</details>
