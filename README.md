# libopenweathermap_client
this Program is openweathermap client library.  
  
Dependents my libhttp_connector. So before build must do 'git submodule init' and 'git submodule update'.  
  
using build tool of CMake.  
  
required JSON-C  
# Build
### First (If you already do that skip.)
```
git submodule init　＆＆　git submodule update
```

### 
```
mkdir -p build && cd build && cmake .. && cmake --build .
```

# Usage
link this library then call function of get_openweather_map_current_data(openweather_query_s *query)
```c
  openweather_query_s query = {};
  query.api_key = "your api key";

  const char *city_name = "City Name";
  ssize_t city_name_size = strlen(city_name);
  query.city_name = INIT_ARRAY(char, city_name_size + 1);
  strncpy(query.city_name, city_name, city_name_size);
  query.city_name[city_name_size] = '\0';

  openweather_map_current_s *result = get_openweather_map_current_data(&query);
 
```

openweather_query_s is data struct for GET query. But current support only city name and api key. 
```c
typedef struct OpenWeatherMapQueryStruct {
  char *city_name;
  int city_id;
  char *country_name;
  int country_code;
  char *api_key;
  int state_code;
  char *units;
  char *mode;
  char *lang;
  int lat;
  int lon;
  int zip_code;
  char *bbox;
} openweather_query_s;
```

get result value of type is openweather_map_current_s.
```c
typedef struct OpenWeatherMapCurrent {
  openweather_coord_s *coord;
  openweather_weather_s *weather;
  char *base;
  openweather_main_s *main;
  long long visibility;
  openweather_wind_s *wind;
  int clouds;
  openweather_rain_s *rain;
  openweather_snow_s *snow;
  long long dt;
  openweather_sys_s *sys;
  long long timezone;
  long long id;
  char *name;
  int cod;
} openweather_map_current_s;
```
