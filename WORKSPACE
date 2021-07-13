workspace(name = "rules_scala_proto")

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

skylib_version = "1.0.3"
http_archive(
    name = "bazel_skylib",
    sha256 = "1c531376ac7e5a180e0237938a2536de0c54d93f5c278634818e0efc952dd56c",
    type = "tar.gz",
    url = "https://mirror.bazel.build/github.com/bazelbuild/bazel-skylib/releases/download/{}/bazel-skylib-{}.tar.gz".format(skylib_version, skylib_version),
)

rules_scala_version = "5df8033f752be64fbe2cedfd1bdbad56e2033b15"

http_archive(
    name = "io_bazel_rules_scala",
    sha256 = "b7fa29db72408a972e6b6685d1bc17465b3108b620cb56d9b1700cf6f70f624a",
    strip_prefix = "rules_scala-%s" % rules_scala_version,
    type = "zip",
    url = "https://github.com/bazelbuild/rules_scala/archive/%s.zip" % rules_scala_version,
)

load("@io_bazel_rules_scala//:scala_config.bzl", "scala_config")
scala_config()

http_archive(
    name = "com_google_protobuf",
    sha256 = "cf754718b0aa945b00550ed7962ddc167167bd922b842199eeb6505e6f344852",
    strip_prefix = "protobuf-3.11.3",
    urls = [
        "https://mirror.bazel.build/github.com/protocolbuffers/protobuf/archive/v3.11.3.tar.gz",
        "https://github.com/protocolbuffers/protobuf/archive/v3.11.3.tar.gz",
    ],
)

http_archive(
    name = "rules_cc",
    sha256 = "29daf0159f0cf552fcff60b49d8bcd4f08f08506d2da6e41b07058ec50cfeaec",
    strip_prefix = "rules_cc-b7fe9697c0c76ab2fd431a891dbb9a6a32ed7c3e",
    urls = ["https://github.com/bazelbuild/rules_cc/archive/b7fe9697c0c76ab2fd431a891dbb9a6a32ed7c3e.tar.gz"],
)

http_archive(
    name = "rules_java",
    sha256 = "220b87d8cfabd22d1c6d8e3cdb4249abd4c93dcc152e0667db061fb1b957ee68",
    urls = ["https://github.com/bazelbuild/rules_java/releases/download/0.1.1/rules_java-0.1.1.tar.gz"],
)

http_archive(
    name = "rules_proto",
    sha256 = "8e7d59a5b12b233be5652e3d29f42fba01c7cbab09f6b3a8d0a57ed6d1e9a0da",
    strip_prefix = "rules_proto-7e4afce6fe62dbff0a4a03450143146f9f2d7488",
    urls = [
        "https://mirror.bazel.build/github.com/bazelbuild/rules_proto/archive/7e4afce6fe62dbff0a4a03450143146f9f2d7488.tar.gz",
        "https://github.com/bazelbuild/rules_proto/archive/7e4afce6fe62dbff0a4a03450143146f9f2d7488.tar.gz",
    ],
)

http_archive(
    name = "rules_python",
    sha256 = "e5470e92a18aa51830db99a4d9c492cc613761d5bdb7131c04bd92b9834380f6",
    strip_prefix = "rules_python-4b84ad270387a7c439ebdccfd530e2339601ef27",
    urls = ["https://github.com/bazelbuild/rules_python/archive/4b84ad270387a7c439ebdccfd530e2339601ef27.tar.gz"],
)

http_archive(
    name = "zlib",
    build_file = "@com_google_protobuf//third_party:zlib.BUILD",
    sha256 = "c3e5e9fdd5004dcb542feda5ee4f0ff0744628baf8ed2dd5d66f8ca1197cb1a1",
    strip_prefix = "zlib-1.2.11",
    urls = [
        "https://mirror.bazel.build/zlib.net/zlib-1.2.11.tar.gz",
        "https://zlib.net/zlib-1.2.11.tar.gz",
    ],
)

register_toolchains("//:custom_scala_toolchain")

register_toolchains("@io_bazel_rules_scala//scala_proto:default_toolchain")
register_toolchains("//:custom_proto_deps_toolchain")
load("@bazel_tools//tools/build_defs/repo:git.bzl", "git_repository")

RULES_JVM_EXTERNAL_TAG = "3.2"

RULES_JVM_EXTERNAL_SHA = "82262ff4223c5fda6fb7ff8bd63db8131b51b413d26eb49e3131037e79e324af"

http_archive(
    name = "rules_jvm_external",
    sha256 = RULES_JVM_EXTERNAL_SHA,
    strip_prefix = "rules_jvm_external-%s" % RULES_JVM_EXTERNAL_TAG,
    url = "https://github.com/bazelbuild/rules_jvm_external/archive/%s.zip" % RULES_JVM_EXTERNAL_TAG,
)


load("@rules_jvm_external//:defs.bzl", "maven_install")
load("@rules_jvm_external//:specs.bzl", "maven")

maven_install(
    artifacts = [
        "org.scala-lang:scala-library:jar:2.12.11",
        "org.scala-lang:scala-reflect:jar:2.12.11",
        "org.scala-lang:scala-compiler:jar:2.12.11",

        # common
        "org.scala-lang.modules:scala-xml_2.12:1.0.5",
        "org.scala-lang.modules:scala-parser-combinators_2.12:1.0.5",

        # proto
        "com.thesamet.scalapb:compilerplugin_2.12:0.9.7",
        "com.thesamet.scalapb:protoc-bridge_2.12:0.7.14",
        "com.thesamet.scalapb:scalapbc_2.12:0.9.7",
        "com.thesamet.scalapb:scalapb-runtime_2.12:0.9.7",
        "com.thesamet.scalapb:scalapb-runtime-grpc_2.12:0.9.7",
        "com.thesamet.scalapb:lenses_2.12:0.9.7",
        "com.lihaoyi:fastparse_2.12:2.1.3",
        "io.grpc:grpc-core:1.24.0",
        "io.grpc:grpc-api:1.24.0",
        "io.grpc:grpc-protobuf:1.24.0",
        "io.grpc:grpc-netty:1.24.0",
        "io.grpc:grpc-context:1.24.0",
        "io.perfmark:perfmark-api:0.17.0",
        "com.google.guava:guava:26.0-android",
        "com.google.instrumentation:instrumentation-api:0.3.0",
        "io.netty:netty-codec:4.1.32.Final",
        "io.netty:netty-codec-http:4.1.32.Final",
        "io.netty:netty-codec-socks:4.1.32.Final",
        "io.netty:netty-codec-http2:4.1.32.Final",
        "io.netty:netty-handler:4.1.32.Final",
        "io.netty:netty-buffer:4.1.32.Final",
        "io.netty:netty-transport:4.1.32.Final",
        "io.netty:netty-resolver:4.1.32.Final",
        "io.netty:netty-common:4.1.32.Final",
        "io.netty:netty-handler-proxy:4.1.32.Final",
        "io.opencensus:opencensus-api:0.22.1",
        "io.opencensus:opencensus-impl:0.22.1",
        "com.lmax:disruptor:3.4.2",
        "io.opencensus:opencensus-impl-core:0.22.1",
        "io.opencensus:opencensus-contrib-grpc-metrics:0.22.1",

        "org.scalameta:common_2.12:jar:4.3.0",
        "org.scalameta:fastparse_2.12:jar:1.0.1",
        "org.scalameta:fastparse-utils_2.12:jar:1.0.1",
        "org.scala-lang.modules:scala-collection-compat_2.12:jar:2.1.2",
        "org.scalameta:parsers_2.12:jar:4.3.0",
        "org.scalameta:scalafmt-core_2.12:jar:2.3.2",
        "org.scalameta:scalameta_2.12:jar:4.3.0",
        "org.scalameta:trees_2.12:jar:4.3.0",
        "org.typelevel:paiges-core_2.12:jar:0.2.4",
        "com.typesafe:config:1.3.3",
        "org.scala-lang:scalap:jar:2.11.12",
        "com.thesamet.scalapb:lenses_2.12:jar:0.9.0",
        "com.thesamet.scalapb:scalapb-runtime_2.12:jar:0.9.0",
        "com.lihaoyi:fansi_2.12:jar:0.2.5",
        "com.lihaoyi:pprint_2.12:jar:0.5.3",
        "com.lihaoyi:sourcecode_2.12:jar:0.1.7",
        "com.google.protobuf:protobuf-java:3.10.0",
        "com.geirsson:metaconfig-core_2.12:jar:0.9.4",
        "com.geirsson:metaconfig-typesafe-config_2.12:jar:0.9.4",
    ],
    fetch_sources = True,
    generate_compat_repositories = True,
    maven_install_json = "@//:maven_install.json",
    repositories = [
        "https://jcenter.bintray.com/",
        "https://maven.google.com",
        "https://repo1.maven.org/maven2",
    ],
)

load("@maven//:defs.bzl", "pinned_maven_install")

pinned_maven_install()
