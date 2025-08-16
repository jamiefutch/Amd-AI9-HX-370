# llama.cpp

##Compiling llama.cpp on windows

Clone the llama.cpp repo
```
git clone https://github.com/ggml-org/llama.cpp.git
```

Clone the curl repo
```
git clone https://github.com/curl/curl.git
```

Clone and bootstrap vcpkg (if you haven't already)

[More info here](https://curl.se/docs/install.html)
```
git clone https://github.com/microsoft/vcpkg.git
cd vcpkg
.\bootstrap-vcpkg.bat

./vcpkg integrate install
./vcpkg install curl[tool]
```

Install dependencies
```
.\vcpkg install zlib brotli zstd nghttp2 libidn2 libpsl
```

Use vcpkg toolchain when configuring curl
```
cd ..\curl
mkdir build
cd build
cmake .. -DCMAKE_TOOLCHAIN_FILE=C:/path/to/vcpkg/scripts/buildsystems/vcpkg.cmake

## in my case--> cmake .. -DCMAKE_TOOLCHAIN_FILE=C://projects//vcpkg//scripts//buildsystems//vcpkg.cmake
```

Build
```
cmake --build . --config Release
```


## CMakeLists.txt

[Example CMakeLists.txt modified for windows](./CMakeLists.txt)

The placement of the snippet below shows the position that works
```
#####################################################
##
## BEGIN Modified for working on windows
##
#####################################################

set(CURL_LIBRARY "C:\\projects\\vcpkg\\packages\\curl_x64-windows\\lib")
#set(CURL_INCLUDE_DIR "C:\\projects\\curl-bin\\include\\")	
set(CURL_INCLUDE_DIR "C:\\projects\\vcpkg\\packages\\curl_x64-windows\\include\\")	

find_package(CURL REQUIRED)
#find_package(CURL REQUIRED) target_link_libraries(llama CURL::libcurl)

include_directories(${CURL_INCLUDE_DIR})
#target_link_libraries(llama ${CURL_LIBRARY})

#####################################################
##
## END Modified for working on windows
##
#####################################################
```

Build llama.cpp as the in the llama.cpp docs.