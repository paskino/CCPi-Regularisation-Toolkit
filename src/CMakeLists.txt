#   Copyright 2017 Edoardo Pasca
#
#   Licensed under the Apache License, Version 2.0 (the "License");
#   you may not use this file except in compliance with the License.
#   You may obtain a copy of the License at
#
#       http://www.apache.org/licenses/LICENSE-2.0
#
#   Unless required by applicable law or agreed to in writing, software
#   distributed under the License is distributed on an "AS IS" BASIS,
#   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
#   See the License for the specific language governing permissions and
#   limitations under the License.
add_subdirectory(Core)
if (BUILD_MATLAB_WRAPPER)
    add_subdirectory(Matlab)
endif()
if (BUILD_PYTHON_WRAPPER)
    add_subdirectory(Python)
endif()
find_package(OpenMP REQUIRED)
if (OPENMP_FOUND)
    set (CMAKE_C_FLAGS "${CMAKE_C_FLAGS} ${OpenMP_C_FLAGS}")
    set (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${OpenMP_CXX_FLAGS}")
    set (CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} ${OpenMP_EXE_LINKER_FLAGS} ${OpenMP_CXX_FLAGS}")
   set (CMAKE_SHARED_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} ${OpenMP_SHARED_LINKER_FLAGS} ${OpenMP_CXX_FLAGS}")
   set (CMAKE_STATIC_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} ${OpenMP_STATIC_LINKER_FLAGS} ${OpenMP_CXX_FLAGS}")
endif()
