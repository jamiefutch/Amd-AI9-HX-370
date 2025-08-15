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


## CMakeLists.txt

[Example CMakeLists.txt modified for windows](./CMakeLists.txt)

The placement of the snippet below shows the position that works
```
#####################################################
##
## BEGIN Modified for working on windows
##
#####################################################

set(CURL_LIBRARY "C:/projects/curl-bin/bin/curl.exe")
set(CURL_INCLUDE_DIR "C:/projects/curl-bin/include/")	## set to local llama.cpp repo
include_directories(${CURL_INCLUDE_DIR})
#target_link_libraries(your_target_name ${CURL_LIBRARY})

#####################################################
##
## END Modified for working on windows
##
#####################################################
```

Build llama.cpp as the in the llama.cpp docs.