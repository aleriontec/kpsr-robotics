#****************************************************************************
#
#                           Klepsydra Core Modules
#              Copyright (C) 2019-2020  Klepsydra Technologies GmbH
#                            All Rights Reserved.
#
#  This file is subject to the terms and conditions defined in
#  file 'LICENSE.md', which is part of this source code package.
#
#  NOTICE:  All information contained herein is, and remains the property of Klepsydra
#  Technologies GmbH and its suppliers, if any. The intellectual and technical concepts
#  contained herein are proprietary to Klepsydra Technologies GmbH and its suppliers and
#  may be covered by Swiss and Foreign Patents, patents in process, and are protected by
#  trade secret or copyright law. Dissemination of this information or reproduction of
#  this material is strictly forbidden unless prior written permission is obtained from
#  Klepsydra Technologies GmbH.
#
#****************************************************************************

SET(PROJ_NAME kpsr_mem_${PROJ_MAIN_NAME}_tests)
PROJECT(${PROJ_NAME})

# Include directories with headers
#---------------------------------------------------#
INCLUDE_DIRECTORIES( ${CMAKE_CURRENT_SOURCE_DIR}/include )
INCLUDE_DIRECTORIES( ${CMAKE_SOURCE_DIR}/${PROJ_MAIN_NAME}/modules/${PROJ_MAIN_NAME}/include )
INCLUDE_DIRECTORIES( ${CMAKE_SOURCE_DIR}/${PROJ_MAIN_NAME}/tests/common )
INCLUDE_DIRECTORIES( ${CMAKE_SOURCE_DIR}/${PROJ_MAIN_NAME}/modules/mem_mdlw/include )
INCLUDE_DIRECTORIES( ${KLEPSYDRA_INCLUDE_DIRS} )

# Source
#---------------------------------------------------#
FILE(GLOB ${PROJ_NAME}_SRC
    "src/*.cpp"
)

# Link libraries with Project
#---------------------------------------------------#
LINK_DIRECTORIES(${KPSR_LIBRARY_PATH})
ADD_EXECUTABLE(${PROJ_NAME} ${${PROJ_NAME}_HEADERS} ${${PROJ_NAME}_SRC} ) 

#---------------------------------------------------#
TARGET_LINK_LIBRARIES(${PROJ_NAME} 
    ${KLEPSYDRA_CORE_LIBRARIES}
    gtest_main 
    kpsr_mem_${PROJ_MAIN_NAME} 
    ${OpenCV_LIBS})

add_test(NAME ${PROJ_NAME} COMMAND ${PROJ_NAME})
