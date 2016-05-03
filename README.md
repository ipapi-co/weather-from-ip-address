
### Recipe to get weather forecast from an IP address

### Ingredients 
- IP address to location API : ipapi.co (free, no key required)
- Weather API : openweathermap.org (free but requires key, signup to get one)

### Ruby
```ruby
require 'net/http'
require 'json'

$ip = '208.67.222.222'

$latlong = Net::HTTP.get(URI('https://ipapi.co/' + $ip + '/latlong/')).split(",")

$weather = JSON.parse(Net::HTTP.get(URI('http://api.openweathermap.org/data/2.5/weather?lat='+$latlong[0]+'&lon='+$latlong[1]+'&appid='+$API_KEY)))
```

### Python
```python
from requests import get

ip = '208.67.222.222'

latlong = get('https://ipapi.co/{}/latlong/'.format(ip)).text.split(',')

weather = get('http://api.openweathermap.org/data/2.5/weather?lat={}&lon={}&appid=API_KEY'.format(latlong[0], latlong[1])).json()
```

