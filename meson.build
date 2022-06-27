
project('glfw', 'c',
    version: '3.3.0',
    license: 'zlib')

cc = meson.get_compiler('c')
compiler_id = cc.get_id()

math_dep = cc.find_library('m', required: false)
rt_dep = cc.find_library('rt', required: false)
threads_dep = dependency('threads')


#--------------------------------------------------------------------
# Detect and select backend APIs
#--------------------------------------------------------------------

host_system = host_machine.system()

backend = get_option('glfw_backend')
if backend == 'auto'
    if host_system == 'windows' or host_system == 'cygwin'
        backend = 'win32'
    elif host_system == 'darwin'
        backend = 'cocoa'
    elif host_system == 'linux' or host_system == 'bsd'
        backend = 'x11'
    else
        error('Unable to determine the backend automatically.')
    endif
endif


#--------------------------------------------------------------------
# Add subdirectories
#--------------------------------------------------------------------

subdir('deps')
subdir('src')

if get_option('glfw_build_tests')
    subdir('tests')
endif

if get_option('glfw_build_examples')
    subdir('examples')
endif

if get_option('glfw_build_docs')
    subdir('docs')
endif
