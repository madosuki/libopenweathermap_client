# libopenweathermap_client
this Program is openweathermap client library.  
  
Dependents my libhttp_connector. So before build must do 'git submodule init' and 'git submodule update'.  
  
using build tool of CMake.  
  
required JSON-C  
#Build
## First (If you already do that skip.)
```
git submodule init
```

## Second
```
git submodule update
```

## Third
```
mkdir -p build && cd build && cmake .. && cmake --build .
```
