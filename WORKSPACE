workspace(name = "grpc_test_repo")

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")
load("@bazel_tools//tools/build_defs/repo:git.bzl", "git_repository")

# Download the rules_docker repository at release v0.10.0
http_archive(
    name = "io_bazel_rules_docker",
    sha256 = "7d453450e1eb70e238eea6b31f4115607ec1200e91afea01c25f9804f37e39c8",
    strip_prefix = "rules_docker-0.10.0",
    urls = ["https://github.com/bazelbuild/rules_docker/releases/download/v0.10.0/rules_docker-v0.10.0.tar.gz"],
)

# OPTIONAL: Call this to override the default docker toolchain configuration.
# This call should be placed BEFORE the call to "container_repositories" below
# to actually override the default toolchain configuration.
# Note this is only required if you actually want to call
# docker_toolchain_configure with a custom attr; please read the toolchains
# docs in /toolchains/docker/ before blindly adding this to your WORKSPACE.

load(
    "@io_bazel_rules_docker//repositories:repositories.bzl",
    container_repositories = "repositories",
)
container_repositories()

load(
    "@io_bazel_rules_docker//python:image.bzl",
    _py_image_repos = "repositories",
)

_py_image_repos()

load(
    "@io_bazel_rules_docker//python3:image.bzl",
    _py3_image_repos = "repositories",
)

_py3_image_repos()

git_repository(
    name = "com_apt_itude_rules_pip",
    commit = "e5ed5e72bf5a7521244e1d2119821628bbf17263",
    remote = "https://github.com/apt-itude/rules_pip.git",
)

load("@com_apt_itude_rules_pip//rules:dependencies.bzl", "pip_rules_dependencies")

pip_rules_dependencies()

load("@com_apt_itude_rules_pip//rules:repository.bzl", "pip_repository")

pip_repository(
    name = "local_deps",
    python_interpreter = "python2",
    requirements = "@grpc_test_repo//:requirements.txt",
)

pip_repository(
    name = "local_py3_deps",
    python_interpreter = "python3",
    requirements = "@grpc_test_repo//:requirements.txt",
)

load("@io_bazel_rules_docker//container:container.bzl", "container_image", "container_pull")


container_pull(
  name = "ubuntu_py3",
  registry = "161262502093.dkr.ecr.us-east-1.amazonaws.com",
  repository = "avmaps-freshness",
  digest = "sha256:3d9a564b2a98f2cee45b29dfcfb8791ca62c772b33e0efe23c49e79926e5819c",
)
