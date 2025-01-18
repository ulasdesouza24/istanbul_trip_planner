```markdown
# Istanbul Trip Planner

## Overview
This project is an AI-powered trip planner for Istanbul that creates customized daily itineraries. It takes into account factors such as traffic conditions, attraction opening hours, and optimal visit durations to generate a comprehensive travel schedule.

## Features
- Generates detailed day trip itineraries for Istanbul
- Calculates travel times between locations considering traffic patterns
- Provides comprehensive information about tourist attractions
- Includes recommendations for activities, photo spots, and dining
- Optimizes route based on opening hours and visit durations

## Prerequisites
The following packages need to be installed:
```bash
pip install smolagents
pip install googlemaps
```

You'll also need:
- A Google Maps API key
- A Hugging Face API token

## Configuration
1. Set your Hugging Face API token:
```python
os.environ["HUGGING_FACE_HUB_TOKEN"] = "your_token_here"
```

2. Configure your Google Maps API key in the `get_istanbul_travel_duration` function.

## Components

### 1. Travel Duration Calculator
- Uses Google Maps API to calculate travel times
- Adjusts duration based on time of day
- Accounts for Istanbul traffic patterns
- Morning rush hour (7-10 AM): 80% longer
- Evening rush hour (4-8 PM): 100% longer

### 2. Attraction Information Database
Includes details about major Istanbul attractions:
- Visit duration recommendations
- Opening hours
- Brief descriptions
- Location-specific tips

### 3. Trip Planner
Creates optimized itineraries considering:
- Start time preferences
- Travel durations
- Attraction opening hours
- Meal breaks
- Traffic conditions

## Usage Example
```python
from smolagents import CodeAgent, HfApiModel, tool

# Initialize the agent
agent = CodeAgent(
    tools=[get_istanbul_travel_duration, get_attraction_info, plan_day_trip],
    model=HfApiModel(),
    additional_authorized_imports=["datetime"]
)

# Generate a trip plan starting at 9 AM
result = agent.run("Can you create a detailed route in Istanbul starting from 9 AM tomorrow?")
print(result)
```

## Sample Output
```
Detailed itinerary with manual information and recommendations:

1. 9:00 AM - Blue Mosque (Sultanahmet)
   Information: The Sultan Ahmed Mosque...
   Recommendation: Visit in the early morning...

2. 11:00 AM - Hagia Sophia
   Information: Former Orthodox basilica...
   Recommendation: Explore the interior...

[Additional locations...]
```

## Limitations
- Requires valid API keys for full functionality
- Limited to predefined tourist attractions
- Weather conditions not considered
- Limited customization options

## Future Improvements
- Add weather integration
- Expand attraction database
- Include public transportation options
- Add user preference customization
- Implement multi-day trip planning
- Add budget considerations
- Include seasonal adjustments

## Contributing
Contributions are welcome! Please feel free to submit a Pull Request.

## License
This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments
- Google Maps API for travel time calculations
- Hugging Face for AI model support
- Contributors to the smolagents library
```
