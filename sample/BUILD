load("@io_bazel_rules_docker//python:image.bzl", "py_image")
load("@io_bazel_rules_docker//python3:image.bzl", "py3_image")
load("@io_bazel_rules_docker//container:push.bzl", "container_push")

py_binary(
  name = "sample",
  srcs = ["sample.py"],
  deps = [
      "@local_py3_deps//grpcio",
  ],
  # if python_version is changed to PY2, there is a cython error.
  # python_version = "PY3",
  python_version = "PY2",
)

py_binary(
  name = "sample_py2",
  srcs = ["sample_py2.py"],
  deps = [
      "@local_deps//grpcio",
  ],
  # if python_version is changed to PY2, there is a cython error.
  # python_version = "PY3",
  python_version = "PY2",
)

py_image(
  name = "sample_image",
  srcs = ["sample.py"],
  deps = [
    "@local_deps//grpcio",
  ],
  main = "sample.py",
)

py3_image(
  name = "sample_py3_image",
  srcs = ["sample.py"],
  deps = [
    "@local_py3_deps//grpcio",
  ],
  main = "sample.py",
)

# Sample Docker Container push
container_push(
  name = "push",
  format = "Docker",
  image = ":sample_image",
  registry = "161262502093.dkr.ecr.us-east-1.amazonaws.com",
  repository = "avmaps-freshness",
  tag = "sample_image",
)
