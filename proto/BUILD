load("@rules_proto_grpc//python:defs.bzl", "python_proto_library", "python_grpc_library")

python_proto_library(
  name = "a_py_proto",
  deps = [":a_proto"],
)

python_proto_library(
  name = "b_py_proto",
  deps = [":b_proto"],
)

proto_library(
  name = "a_proto",
  srcs = ["a.proto"],
)

proto_library(
  name = "b_proto",
  srcs = ["b.proto"],
  deps = [":a_proto"],
)

proto_library(
  name = "s_proto",
  srcs = ["s.proto"],
)

python_grpc_library(
  name = "s_py_proto",
  deps = [":s_proto"],
)
