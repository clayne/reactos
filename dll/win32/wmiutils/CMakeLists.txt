
spec2def(wmiutils.dll wmiutils.spec)

list(APPEND SOURCE
    main.c
    path.c
    statuscode.c
    ${CMAKE_CURRENT_BINARY_DIR}/wmiutils.def)

add_library(wmiutils MODULE ${SOURCE} wmiutils.rc)
set_module_type(wmiutils win32dll)
target_link_libraries(wmiutils wine)
add_importlibs(wmiutils oleaut32 msvcrt kernel32 ntdll)
add_cd_file(TARGET wmiutils DESTINATION reactos/system32/wbem FOR all)
set_wine_module_FIXME(wmiutils) # CORE-5743: No CONST_VTABLE
