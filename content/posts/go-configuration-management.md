---
title: 'wc-toolkit'
date: 2024-04-01T13:43:53-06:00
draft: false
# image: brand_image.jpg
tags: ["go", "project"]
# series: "How to use poison"
---
# Working with configuration files in Go.
Modern applications typically necessitate various configurations, tailored to each specific environment like development, testing, and production. These configurations often encompass service account credentials and links to supporting services, including databases. In modern web development can be very complex to say the least, when it comes to development and configuration, using the twelve-factor app methodology Let’s see how we can use Viper when it comes to environment configuration.

Using Viper in this example we created a Func that we set up our configuration files with different environments and different types of file types as well. Let’s step through each of the following to better understand why and how we might use Viper when it comes to different settings, and configurations.

```go
func Configurations() (environment string, err error) {
var env = os.Getenv("ENV")

viper.SetConfigName(env)             
viper.SetConfigType("yaml")          
viper.AddConfigPath("../../config/")
 
if env == "prod" {
  viper.SetEnvPrefix("prod") // Set the prefix for environment variables
} else {
  viper.SetEnvPrefix("dev") // Set the prefix for environment variables
}

viper.AutomaticEnv()
viper.SetEnvKeyReplacer(strings.NewReplacer(".", "_")) 

err = viper.ReadInConfig() 
if err != nil {
 log.Fatalf("Fatal error config file: %s \\n", err)
}

return env, err
}
```

## Function Signature
With this function we are returning two things an envionment and or error

func Configurations() (environment string, err error) {}
With this approach, we reduce the some complexity on our entry point being our main() func that we will call during start-up. This declares a function named Configurations that returns two values: an environment string and an error object.

This will also help so that we only need to all this call this once and our Viper configuration will have all of our predefined configurations in one location.

## Retrieve Environment Variable
`var env = os.Getenv("ENV")`
Here we have the environment configuration which we are passing in by an environment variable. In modern systems this is typically done via CI/CD or something similar. If we not stick with the notion that we are passing this in via a CI/CD method this is easy to modify based on different pipelines.

Let’s say that we are have the following; from here we are able to use this so that we can certain behavior based on the environment itself. In the following example we are looking for the environment variable ENV based on this we can now use this later on to set conditions that may defer from staging , dev and or prod .

## Configure Viper
```go
viper.SetConfigName(env)             
viper.SetConfigType("yaml")          
viper.AddConfigPath("../../config/")
```

These lines configure the viper library:

- `SetConfigName(env)`: Sets the name of the configuration file to the value of `env`. This means viper will look for a file named after the current environment (e.g., `dev.yaml or prod.yaml`).
- `SetConfigType("yaml")`: Specifies that the configuration files are in YAML format.
- `AddConfigPath("../../config/")`: Sets the path to the directory where the configuration files are located, relative to the current working directory.
## Environment-Specific Settings
```go
if env == "prod" {
    viper.SetEnvPrefix("prod") 
} else {
    viper.SetEnvPrefix("dev") 
}
```
Depending on whether the environment is production ("prod") or not, it sets a prefix for environment variables using viper.SetEnvPrefix. This prefix is used by viper to distinguish environment variables specific to each environment.

## Automatic Environment Variables
```go
viper.AutomaticEnv()
viper.SetEnvKeyReplacer(strings.NewReplacer(".", "_"))
viper.AutomaticEnv() 
```

tells viper to automatically override configuration file settings 
with the values of any matching environment variables ie `DEV_CRDB_USER` using the prefix that we set in the last section. `viper.SetEnvKeyReplacer` allows you to define a string replacer for environment variable names, in this case, replacing periods (`"."`) with underscores (`"_"`).

## Read Configuration
```go
err = viper.ReadInConfig()
if err != nil {
    log.Fatalf("Fatal error config file: %s \\n", err)
}
```

`viper.ReadInConfig()` attempts to read the configuration file based on the previously set parameters. If an error occurs (e.g., file not found, parsing error), it logs a fatal error and terminates the program.

# Return Values
```go
return env, err
```
Finally, the function returns the env string and any error encountered during the configuration reading process.