CMAKE_<LANG>_IMPLICIT_LINKER_SEARCH_DIRECTORIES
-----------------------------------------------

Implicit linker search directories detected for language ``<LANG>``.

The paths searched by the linker for shared libraries referenced in
other shared libraries can differ from the implicit link directories (which
are a property of the compiler's specs, and not of the linker).

This happens, for example, when using a custom compiler with the system
linker.  In this instance, filtering out directories based on the contents
of CMAKE_<LANG>_IMPLICIT_LINK_DIRECTORIES can lead to paths that need to
be passed via (for example) -Wl,-rpath and -Wl,-rpath-link being dropped.
Instead, CMake filters these linker-specific arguments using this variable.

If the linker does not or cannot report values for this, it defaults to
CMAKE_<LANG>_IMPLICIT_LINK_DIRECTORIES instead.

When one of these directories is referenced in a linker-specific argument
such as -Wl,-rpath and -Wl,-rpath-link, CMake will silently drop that
argument or path from that argument.
