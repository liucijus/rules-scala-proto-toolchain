load("@io_bazel_rules_scala//scala:scala.bzl", "scala_binary", "scala_library", "scala_test")
load("@io_bazel_rules_scala//scala:scala_toolchain.bzl", "scala_toolchain")
load("@io_bazel_rules_scala//scala:providers.bzl", "declare_deps_provider")

scala_toolchain(
    name = "warn_unused_deps_scala_toolchain",
    dep_providers = [
        ":scala_xml_provider",
        ":parser_combinators_provider",
        ":scala_compile_classpath_provider",
        ":scala_library_classpath_provider",
        ":scala_macro_classpath_provider",
    ],
    dependency_mode = "plus-one",
    dependency_tracking_method = "ast",
    strict_deps_mode = "warn",
    unused_dependency_checker_mode = "warn",
    visibility = ["//visibility:public"],
)

toolchain(
    name = "custom_scala_toolchain",
    toolchain = "warn_unused_deps_scala_toolchain",
    toolchain_type = "@io_bazel_rules_scala//scala:toolchain_type",
    visibility = ["//visibility:public"],
)

declare_deps_provider(
    name = "scala_xml_provider",
    deps_id = "scala_xml",
    visibility = ["//visibility:public"],
    deps = ["@maven//:org_scala_lang_modules_scala_xml_2_13"],
)

declare_deps_provider(
    name = "parser_combinators_provider",
    deps_id = "parser_combinators",
    visibility = ["//visibility:public"],
    deps = ["@maven//:org_scala_lang_modules_scala_parser_combinators_2_13"],
)

declare_deps_provider(
    name = "scala_compile_classpath_provider",
    deps_id = "scala_compile_classpath",
    visibility = ["//visibility:public"],
    deps = [
        "@maven//:org_scala_lang_scala_compiler",
        "@maven//:org_scala_lang_scala_library",
        "@maven//:org_scala_lang_scala_reflect",
    ],
)

declare_deps_provider(
    name = "scala_library_classpath_provider",
    deps_id = "scala_library_classpath",
    visibility = ["//visibility:public"],
    deps = [
        "@maven//:org_scala_lang_scala_library",
        "@maven//:org_scala_lang_scala_reflect",
    ],
)

declare_deps_provider(
    name = "scala_macro_classpath_provider",
    deps_id = "scala_macro_classpath",
    visibility = ["//visibility:public"],
    deps = [
        "@maven//:org_scala_lang_scala_library",
        "@maven//:org_scala_lang_scala_reflect",
    ],
)

# scala proto deps toolchain
load("@io_bazel_rules_scala//scala_proto:scala_proto_toolchain.bzl", "scala_proto_deps_toolchain")
load("@io_bazel_rules_scala//scala:providers.bzl", "declare_deps_provider")

scala_proto_deps_toolchain(
    name = "proto_deps_toolchain_impl",
    dep_providers = [
        ":custom_grpc_deps",
        ":custom_compile_deps",
        ":custom_worker_deps",
    ],
    visibility = ["//visibility:public"],
)

toolchain(
    name = "custom_proto_deps_toolchain",
    toolchain = ":proto_deps_toolchain_impl",
    toolchain_type = "@io_bazel_rules_scala//scala_proto:deps_toolchain_type",
    visibility = ["//visibility:public"],
)

declare_deps_provider(
    name = "custom_compile_deps",
    deps_id = "scalapb_compile_deps",
    visibility = ["//visibility:public"],
    deps = [
        "@com_google_protobuf//:protobuf_java",
        "@maven//:com_lihaoyi_fastparse_2_13",
        "@maven//:com_thesamet_scalapb_lenses_2_13",
        "@maven//:com_thesamet_scalapb_scalapb_runtime_2_13",
        "@maven//:io_grpc_grpc_protobuf",
        "@maven//:org_scala_lang_scala_library",
    ],
)

declare_deps_provider(
    name = "custom_grpc_deps",
    deps_id = "scalapb_grpc_deps",
    visibility = ["//visibility:public"],
    deps = [
        "@maven//:com_google_guava_guava",
        "@maven//:com_google_instrumentation_instrumentation_api",
        "@maven//:com_lmax_disruptor",
        "@maven//:com_thesamet_scalapb_scalapb_runtime_grpc_2_13",
        "@maven//:io_grpc_grpc_api",
        "@maven//:io_grpc_grpc_context",
        "@maven//:io_grpc_grpc_core",
        "@maven//:io_grpc_grpc_netty",
        "@maven//:io_grpc_grpc_protobuf",
        "@maven//:io_grpc_grpc_stub",
        "@maven//:io_netty_netty_buffer",
        "@maven//:io_netty_netty_codec",
        "@maven//:io_netty_netty_codec_http",
        "@maven//:io_netty_netty_codec_http2",
        "@maven//:io_netty_netty_codec_socks",
        "@maven//:io_netty_netty_common",
        "@maven//:io_netty_netty_handler",
        "@maven//:io_netty_netty_handler_proxy",
        "@maven//:io_netty_netty_resolver",
        "@maven//:io_netty_netty_transport",
        "@maven//:io_opencensus_opencensus_api",
        "@maven//:io_opencensus_opencensus_contrib_grpc_metrics",
        "@maven//:io_opencensus_opencensus_impl",
        "@maven//:io_opencensus_opencensus_impl_core",
        "@maven//:io_perfmark_perfmark_api",
    ],
)

declare_deps_provider(
    name = "custom_worker_deps",
    deps_id = "scalapb_worker_deps",
    visibility = ["//visibility:public"],
    deps = [
        "@com_google_protobuf//:protobuf_java",
        "@maven//:com_thesamet_scalapb_compilerplugin_2_13",
        "@maven//:com_thesamet_scalapb_protoc_bridge_2_13",
    ],
)
