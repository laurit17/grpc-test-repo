package(default_visibility = ["//visibility:public"])

py_runtime(
    name = "myruntime",
    interpreter_path = select({
        # Update paths as appropriate for your system.
        "@bazel_tools//tools/python:PY2": "/usr/bin/python",
        "@bazel_tools//tools/python:PY3": "/usr/bin/python3",
    }),
    files = [],
)
