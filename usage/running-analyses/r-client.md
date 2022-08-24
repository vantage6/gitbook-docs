# R Client

It is assumed you installed the [vantage6-client](../../installation/client.md). The R client can create tasks and retrieve their results. If you want to do more administrative tasks, either use the API directly or use the [python-client.md](python-client.md "mention"). Make sure you have got the latest version of the R client package vtg installed by running.
```r
devtools::install_github('IKNL/vtg')
```

Initialization of the R client can be done by:

```r
# load the library
library (vtg)
setup.client <- function() {
  # Username/password should be provided by the administrator of
  # the server.
  username <- "username@example.com"
  password <- "password"
  
  host <- 'https://petronas.vantage6.ai:443'
  api_path <- ''
  
  # Create the client & authenticate
  client <- vtg::Client$new(host, api_path=api_path)
  client$authenticate(username, password)

  return(client)
}

# Create a client
client <- setup.client()

# Get the Collaboration that this client is associated with 
print(client$getCollaborations())

# This flag set to TRUE indicates that the main algorithm can be executed by any of the participating organizations in the collaboration. 
client$setUseMasterContainer(T)

```

Then this client can be used for the different algorithms. Refer to the README in the repository on how to call the algorithm. Usually this includes installing some additional client-side packages for the specific algorithm you are using.

{% hint style="warning" %}
The R client is subject to change. We aim to make it more similar to the Python client.
{% endhint %}

## Example 1

First you need to install the client side of the algorithm by:

```r
devtools::install_github('iknl/vtg.coxph', subdir="src")
```

This is the code to run the coxph:

```r
print( client$getCollaborations() )

# Should output something like this:
#   id     name
# 1  1 ZEPPELIN
# 2  2 PIPELINE

# Select a collaboration
client$setCollaborationId(1)

# Define explanatory variables, time column and censor column
expl_vars <- c("Age","Race2","Race3","Mar2","Mar3","Mar4","Mar5","Mar9",
               "Hist8520","hist8522","hist8480","hist8501","hist8201",
               "hist8211","grade","ts","nne","npn","er2","er4")
time_col <- "Time"
censor_col <- "Censor"

# vtg.coxph contains the function `dcoxph`.
result <- vtg.coxph::dcoxph(client, expl_vars, time_col, censor_col)
```


## Example 2 Running the Summary Algorithm on a dataframe

A summary algorithm exists in the algorithm repository that is build in Python. This algorithm produces summary statistics on a given data frame.
This is the code to run summary algorithm:

```r
# Set the docker image to be run
client$set.task.image("harbor2.vantage6.ai/algorithms/summary:wur")

# Set the task name
client$task.name = "summary"

# Define explanatory variables together with their data types.
# As of now only "numeric" and "categorical" variables are supported in R represented as "n" and "c".
# For example the below code represens 7 variables with numeric and categorical data types in the form of a list.

expl_vars <- c(c("ID","n"),c("Hectares","n"),c("Farm_size","n"),c("Off-farm_income","c"),c("Successor","c"),c("Highest_education","c"),c("Education_this_year","c"))


# Set the data forma to json
client$data_format="json"

# Call the summary function, since the summary function name in the image is called "master". It can be called like below.
result <-client$call("master",columns=expl_vars)

```
