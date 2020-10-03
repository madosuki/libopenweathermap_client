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
