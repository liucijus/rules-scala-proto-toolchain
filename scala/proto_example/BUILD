load("@io_bazel_rules_scala//scala_proto:scala_proto.bzl", "scala_proto_library")
load("@rules_proto//proto:defs.bzl", "proto_library")

proto_library(
    name = "proto_lib",
    srcs = ["some.proto"],
    deps = [],
)

scala_proto_library(
    name = "proto_scala_lib",
    deps = [":proto_lib"],
    visibility = ["//visibility:public"],
)
