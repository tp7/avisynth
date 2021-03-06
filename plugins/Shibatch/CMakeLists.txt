# We need CMake 2.8.11 at least, because we use CMake features
# "Target Usage Requirements" and "Generator Toolset selection"
CMAKE_MINIMUM_REQUIRED( VERSION 2.8.11 )

set(PluginName "Shibatch")
set(ProjectName "Plugin${PluginName}")

# Create library
project(${ProjectName})
list (APPEND SourceFiles
    "dbesi0.c"
    "fft.h"
    "paramlist.h"
    "ssrc.cpp"
    "ssrc.h"
    "ssrc-convert.cpp"
    "ssrc-convert.h"
    "supereq.cpp"
    "supereq.h"
    "shibatch.cpp"
)
add_library(${ProjectName} SHARED ${SourceFiles})
set_target_properties(${ProjectName} PROPERTIES "OUTPUT_NAME" ${PluginName})

# Library dependencies 
add_subdirectory("PFC")
target_link_libraries(${ProjectName} "PFC")

# Include directories
target_include_directories(${ProjectName} PRIVATE ${AvsCore_SOURCE_DIR})

if (MSVC_IDE)    
  # Copy output to a common folder for easy deployment
  add_custom_command(
    TARGET ${ProjectName}
    POST_BUILD
    COMMAND xcopy /Y \"$(TargetPath)\" \"${CMAKE_BINARY_DIR}/Output/plugins\"
  )
endif()