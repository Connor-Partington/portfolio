# Surferport 

## Resource description

The Surf Report API lets you find information about surfing conditions, including surf height, water temperature, wind speed, and tide level. It also gives an overall recommendation on if you should go surfing. 

## Endpoints

**GET** /surfreport/**{beachId}**

Get the surf conditions for a specific beach ID.

## Parameters 

### Path parameters

| Parameter | Description |
| :--- | :--- |
| {beachId} | The value for the beach you want to look up. Valid `beachId` values can be found at [surferport.com/beachIds](#surferport). |

### Query string parameters

| Parameter | Required / optional | Type | Description |
| :--- | :--- | :--- | :--- |
| days | Optional | Integer | The number of days to include in the response. Default is 3. Max is 7 |
| time | Optional | Integer. Unix format (ms since 1970. Time zone is GMT or UTC. | The time of the day matching the timezone of the beach. Inlcude the hour to only show conditions for specified hour. |
| units | Optional | Enum | The default unit of measurement. Imperial or Metric. |

## Sample request

    curl -I -X GET "https://api.openweathermap.org/com/surfreport/123?&days=2&units=metrics&hour=1400"

In the example, replace 'APIKEY' with your actual API key.

## Sample response 

This is a sample response from the `surfreport/{beachId}` endpoint:

    {
        "surfreport": [
            {
                "beach": "Santa Cruz",
                "monday": {
                    "1pm": {
                        "tide": 5,
                        "wind": 15,
                        "watertemp": 60,
                        "surfheight": 5,
                        "recommendation": "Go surfing!"
                    },
                    "2pm": {
                        "tide": -1,
                        "wind": 1,
                        "watertemp": 50,
                        "surfheight": 3,
                        "recommendation": "Surfing conditions are okay, not great"
                    }
                    ...

                }
            }
        ]
    }

### Response definitions

The following table describes each item in the response:

| Response item | Description | Data type |
| --- | --- | --- |
| **beach** | The beach you selected based on the beach ID in the request. | String |
| **{day}** | The selected day of the week. | Object |
| **{time}** | The time for the conditions based on the hour. | String |
| {day}/{time}/**tide** | The tide level at the beach based on the specififed day and time. The tide is out when the number is negative, in when the number is positive, and 0 when between states. | Integer |
| {day}/{time}/**wind** | The wind speed at the beach based on the specified day and time.  | Integer |
| {day}/{time}/**watertemp** | The temperature of the water based on the specified day and time. Fahrenheit or Celsius depending on the units of measurement. | Integer |
| {day}/{time}/**surfheight** | The height of the waves based on the specified day and time. | Integer |
| {day}/{time}/**recommendation** | A recommendation on whether to go surfing or not based on a combination of the various factors | String. |

