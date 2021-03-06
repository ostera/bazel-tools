# Copyright 2016-2017 Spotify AB
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
workspace(name = "spotify_bazel_tools")

http_archive(
    name = "io_bazel_rules_go",
    sha256 = "53059e0cda4517afe5a3907f77d1a379577773f2b1659fed8dc668b3f110a7d3",
    strip_prefix = "rules_go-0dc1f9e0741d766780e931d49790ddb501bb34c9",  # branch master
    urls = ["https://github.com/bazelbuild/rules_go/archive/0dc1f9e0741d766780e931d49790ddb501bb34c9.zip"],
)

http_archive(
    name = "io_bazel_rules_scala",
    sha256 = "d25da37320a91c7b5e2e7a2525307a18ed9f21c55fe232ab4423fb73c082357a",
    strip_prefix = "rules_scala-388a2585f45dff804d006b0e81e1b1a1c60578bc",  # branch master
    urls = ["https://github.com/bazelbuild/rules_scala/archive/388a2585f45dff804d006b0e81e1b1a1c60578bc.zip"],
)

http_archive(
    name = "com_github_bazelbuild_buildtools",
    sha256 = "5772dfbd67f6fc7ad8aa07fb5896858d4c65b8aee7a54ada69271b962d69535f",
    strip_prefix = "buildtools-b0f22bba2532e4f62eb815a86637e7ac5372e142",  # branch superhack
    urls = ["https://github.com/dflemstr/buildtools/archive/b0f22bba2532e4f62eb815a86637e7ac5372e142.zip"],
)

load("@io_bazel_rules_go//go:def.bzl", "go_rules_dependencies", "go_register_toolchains")

go_rules_dependencies()

go_register_toolchains()

BAZEL_JAVA_LAUNCHER_VERSION = "0.4.5"

http_file(
    name = "java_stub_template",
    sha256 = "f09d06d55cd25168427a323eb29d32beca0ded43bec80d76fc6acd8199a24489",
    url = ("https://raw.githubusercontent.com/bazelbuild/bazel/" +
           BAZEL_JAVA_LAUNCHER_VERSION +
           "/src/main/java/com/google/devtools/build/lib/bazel/rules/java/" +
           "java_stub_template.txt"),
)

bind(
    name = "io_bazel_rules_scala/dependency/com_google_protobuf/protobuf_java",
    actual = "//3rdparty/jvm/com/google/protobuf:protobuf-java",
)

bind(
    name = "io_bazel_rules_scala/dependency/scala/parser_combinators",
    actual = "//3rdparty/jvm/org/scala-lang/modules:scala-parser-combinators_2_11",
)

bind(
    name = "io_bazel_rules_scala/dependency/scala/scala_compiler",
    actual = "//3rdparty/jvm/org/scala-lang:scala-compiler",
)

bind(
    name = "io_bazel_rules_scala/dependency/scala/scala_library",
    actual = "//3rdparty/jvm/org/scala-lang:scala-library",
)

bind(
    name = "io_bazel_rules_scala/dependency/scala/scala_reflect",
    actual = "//3rdparty/jvm/org/scala-lang:scala-reflect",
)

bind(
    name = "io_bazel_rules_scala/dependency/scala/scala_xml",
    actual = "//3rdparty/jvm/org/scala-lang/modules:scala-xml_2_11",
)

bind(
    name = "io_bazel_rules_scala/dependency/scalatest/scalatest",
    actual = "//3rdparty/jvm/org/scalatest:scalatest_2_11",
)

load("//:tools.bzl", "bazel_tools_repositories")

bazel_tools_repositories()
