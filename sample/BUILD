load("@io_bazel_rules_docker//python:image.bzl", "py_image")
load("@io_bazel_rules_docker//python3:image.bzl", "py3_image")
load("@io_bazel_rules_docker//container:container.bzl", "container_push", "container_image")

container_image(
  name = "ubuntu_py3_base",
  base = "@ubuntu_py3//image",
  ports = ["50051"],
)

py_binary(
  name = "sample",
  srcs = ["sample.py"],
  deps = [
      "@local_py3_deps//grpcio",
  ],
  # if python_version is changed to PY2, there is a cython error.
  python_version = "PY3",
  # python_version = "PY2",
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
  base = ":ubuntu_py3_base",
  srcs = ["sample.py"],
  deps = [
    "@local_deps//grpcio",
  ],
  main = "sample.py",
)

py3_image(
  name = "sample_py3_image",
  srcs = ["sample.py"],
  base = ":ubuntu_py3_base",
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
