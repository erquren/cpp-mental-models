get_filename_component(MODULE_NAME ${CMAKE_CURRENT_SOURCE_DIR} NAME)

file(GLOB SOURCE_FILES "${CMAKE_CURRENT_SOURCE_DIR}/*.cpp")

foreach(CPP_FILE ${SOURCE_FILES})
    get_filename_component(BASENAME ${CPP_FILE} NAME_WE)
    
    # C_MemorySegmentation_main1
    set(TARGET_NAME "${MODULE_NAME}_${BASENAME}")
    
    add_executable(${TARGET_NAME} ${CPP_FILE})
    # main1 intentionally returns a + b, so it is not an exit-code smoke test.
    if(NOT TARGET_NAME STREQUAL "${MODULE_NAME}_main1")
        add_demo_test(${TARGET_NAME})
    endif()
endforeach()
