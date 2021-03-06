# GoFitbit

Wrapper for the OAuth based REST API of Fitbit.com. For the full documentation please see <a href=""http://dev.fitbit.com">dev.fitbit.com</a>.

The development of this library is still in ALPHA so it still could be a bit buggy. So feel free to request merges and bug fix any problems in this repo.

# Usage

Before you can get started with the API you'll have to register your application at <a href="http://dev.fitbit.com">dev.fitbit.com</a> and obtain consumer key and secret for your application.

This library will handle the OAuth authorisation. To register your application you'll have to grant access to your application with your fitbit account. This can be done with the <a href="https://github.com/lenkaiser/gofitbit-client">gofitbit-client</a> repo.

```go
func main() {
	//Init config
	config := &Config{
		false, //Debug
		false, //Disable SSL
	}

	//Initialise FitbitAPI
	fapi, err := NewAPI("--", "--", config)
	if err != nil {
		log.Fatal(err)
	}
	fmt.Println("API initialised")

	//Add client
	client, err := fapi.NewClient()
	if err != nil {
		log.Fatal(err)
	}
	fmt.Println("New client initialised")

	//Call methods from client
	client.GetProfile()
	client.GetRecentActivities()
}
```

# Changelog
- Version 0.4: 08 April 2014
 - Added support for Body, Alarms, Device, Heartrate, Glucose, Water, Sleep
 - Tested 75% of the implemented functions
 - Minor bug fixes (compiler issues, wrong URLs, etc.)
- Version 0.3: 11 March 2014
 - Added support for activities
- Version 0.2: 11 March 2014
 - Fixed to use persisten OAuth token
 - Added data retriever
 - Added Profile struct to retrieve basic profile data
- Version 0.1: 10 March 2014
 - Initial commit
 - Partial support for activities and profile
 - Protected setup so client only calls public methods
 - LICENSE and README.md files