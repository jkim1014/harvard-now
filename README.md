# HarvardNow #
## What it is ##
HarvardNow is an integrated texting service promoting information accessibility at Harvard. Get real time information about services and facilities, including shuttle schedules, laundry timers, and arts events. Text "demo" to (617) 658-4667 to try it out!

## The Services ##

### Laundry ###

#### special ####
Laundry's special function lists all the laundry rooms available to query. Data about each rooom is stored in a separate file within the `laundry` subpackage (`data.py`) and imported on Line 3 of `laundry.py`.

#### eval ####
To evaluate a laundry command, get `roomid` and `machinetype` from the command's arguments and pass them to the `getMachines` function. `getMachines` uses `urllib` and `urllib2` to open the website containing the laundry data and get the HTML, and `beautifulsoup` to parse that HTML and find its relevant parts. We then construct a list of machines, where a machine is represented as a dictionary specifying the machine's `lr` (laundry room id), `id`, `name`, and `time` (a string describing the status of the machine)

### Shuttle ###

#### special ####
Laundry's special function lists all the shuttle stops and routes that the app knows about. This will give new users an idea of what they can find out more about.

#### eval ####
A shuttle command comes in one of two types: `stop` and `route` since the user can ask about either of these. Each of these evaluations basically do the same thing: make an API call with the given arguments and returns them as a string. The code behind making an API call, located in and imported from `api.py`, simply gives the necessary information to the API and returns the restult in JSON format. API stands for Application Program Interface; it is a standard of communication between data sources (in this case, the location of the shuttle data) and the application that wants that data (in this case, our app). Python's `requests` library contains the functions necessary for making an API call. These are converted to JavaScript Object Notation (JSON) format, a standard for representing information as lists and objects (dictionaries).

### Weather ###

#### special ####
Weather's special function simply gives the format that a user should input to receive weather information for a city.

#### eval ####
The weather service works by doing a Google search on the indicated city. It then scrapes the data from the corresponding HTML.

