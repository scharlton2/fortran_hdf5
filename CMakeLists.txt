cmake_minimum_required(VERSION 3.12)
##project (HDF5MyApp C CXX)
project(HDF5MyApp Fortran)

set(LIB_TYPE STATIC) # or SHARED
string(TOLOWER ${LIB_TYPE} SEARCH_TYPE)

#find_package (HDF5 NAMES hdf5 COMPONENTS C ${SEARCH_TYPE})
find_package (HDF5 NAMES hdf5 COMPONENTS Fortran ${SEARCH_TYPE})
#find_package(HDF5) # Find non-cmake built HDF5
set_directory_properties(PROPERTIES INCLUDE_DIRECTORIES "${HDF5_INCLUDE_DIR}")
#set (LINK_LIBS ${LINK_LIBS} ${HDF5_C_${LIB_TYPE}_LIBRARY})
#set (LINK_LIBS ${LINK_LIBS} hdf5::hdf5_fortran_${LIB_TYPE})
set(LINK_LIBS ${LINK_LIBS} hdf5::hdf5_fortran-static)

##set (example cmake_hdf5_test)

##add_executable (${example} ${PROJECT_SOURCE_DIR}/${example}.c)
add_executable (h5_crtdat h5_crtdat.f90)
##TARGET_C_PROPERTIES (${example} PRIVATE ${LIB_TYPE})

target_include_directories(h5_crtdat PRIVATE ${HDF5_INCLUDE_DIR_FORTRAN})

target_link_libraries(h5_crtdat ${LINK_LIBS})

message(STATUS "LINK_LIBS=${LINK_LIBS}")

# hdf5::${hdf5_comp}-${libtype}
# hdf5_comp=hdf5_fortran

message(STATUS "HDF5_INCLUDE_DIR_FORTRAN=${HDF5_Fortran_LIBRARIES}")
message(STATUS "HDF5_Fortran_INCLUDE_DIRS=${HDF5_Fortran_INCLUDE_DIRS}")
message(STATUS "HDF5_INCLUDE_DIR_FORTRAN=${HDF5_INCLUDE_DIR_FORTRAN}")
message(STATUS "HDF5_INCLUDE_DIR_FORTRAN=${HDF5_INCLUDE_DIR_FORTRAN}")
