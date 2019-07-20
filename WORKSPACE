workspace(name = "grpc_book_samples")

# =========================================

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")
load("@bazel_tools//tools/build_defs/repo:git.bzl", "git_repository")

http_archive(
    name = "build_stack_rules_proto",
    urls = ["https://github.com/stackb/rules_proto/archive/b93b544f851fdcd3fc5c3d47aee3b7ca158a8841.tar.gz"],
    sha256 = "c62f0b442e82a6152fcd5b1c0b7c4028233a9e314078952b6b04253421d56d61",
    strip_prefix = "rules_proto-b93b544f851fdcd3fc5c3d47aee3b7ca158a8841",
)

# ================================================================
# Specific Languages Support
# ================================================================

# ----- Load Java dependencies ----
load("@build_stack_rules_proto//:deps.bzl", "io_grpc_grpc_java")

io_grpc_grpc_java()

load("@io_grpc_grpc_java//:repositories.bzl", "grpc_java_repositories")

grpc_java_repositories(omit_com_google_protobuf = True)

load("@build_stack_rules_proto//java:deps.bzl", "java_grpc_library")

java_grpc_library()


# ------ Load Go dependencies ----

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
    name = "io_bazel_rules_go",
    urls = [
        "https://storage.googleapis.com/bazel-mirror/github.com/bazelbuild/rules_go/releases/download/0.18.7/rules_go-0.18.7.tar.gz",
        "https://github.com/bazelbuild/rules_go/releases/download/0.18.7/rules_go-0.18.7.tar.gz",
    ],
    sha256 = "45409e6c4f748baa9e05f8f6ab6efaa05739aa064e3ab94e5a1a09849c51806a",
)

load("@io_bazel_rules_go//go:deps.bzl", "go_rules_dependencies", "go_register_toolchains")

go_rules_dependencies()

go_register_toolchains()

http_archive(
    name = "bazel_gazelle",
    urls = ["https://github.com/bazelbuild/bazel-gazelle/releases/download/0.17.0/bazel-gazelle-0.17.0.tar.gz"],
    sha256 = "3c681998538231a2d24d0c07ed5a7658cb72bfb5fd4bf9911157c0e9ac6a2687",
)

load("@bazel_gazelle//:deps.bzl", "gazelle_dependencies", "go_repository")

gazelle_dependencies()


go_repository(
    name = "com_github_google_uuid",
    importpath = "github.com/google/uuid",
    sha256 = "7e330758f7c81d9f489493fb7ae0e67d06f50753429758b64f25ad5fb2727e21",
    strip_prefix = "uuid-1.1.0",
    urls = ["https://github.com/google/uuid/archive/v1.1.0.tar.gz"],
)

go_repository(
    name = "com_google_cloud_go",
    commit = "7808a7bf89ab1b3b840e00435c5404af438ec24d",
    importpath = "cloud.google.com/go",
    remote = "https://github.com/googleapis/google-cloud-go.git",
    vcs = "git",
)

go_repository(
    name = "org_golang_x_oauth2",
    remote = "https://github.com/golang/oauth2.git",
    vcs = "git",
    commit = "fdc9e635145ae97e6c2cb777c48305600cf515cb",
    importpath = "golang.org/x/oauth2",
)

http_archive(
     name = "com_google_protobuf",
     sha256 = "2244b0308846bb22b4ff0bcc675e99290ff9f1115553ae9671eba1030af31bc0",
     strip_prefix = "protobuf-3.6.1.2",
     urls = ["https://mirror.bazel.build/github.com/google/protobuf/archive/v3.6.1.2.tar.gz",
         "https://github.com/protocolbuffers/protobuf/archive/v3.6.1.2.tar.gz"],
)
