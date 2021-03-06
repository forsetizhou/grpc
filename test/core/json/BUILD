# Copyright 2017, Google Inc.
# All rights reserved.
#
# Redistribution and use in source and binary forms, with or without
# modification, are permitted provided that the following conditions are
# met:
#
#     * Redistributions of source code must retain the above copyright
# notice, this list of conditions and the following disclaimer.
#     * Redistributions in binary form must reproduce the above
# copyright notice, this list of conditions and the following disclaimer
# in the documentation and/or other materials provided with the
# distribution.
#     * Neither the name of Google Inc. nor the names of its
# contributors may be used to endorse or promote products derived from
# this software without specific prior written permission.
#
# THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS
# "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT
# LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR
# A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT
# OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
# SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT
# LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE,
# DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY
# THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
# (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
# OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

licenses(["notice"])  # 3-clause BSD

load("//test/core/util:grpc_fuzzer.bzl", "grpc_fuzzer")

grpc_fuzzer(
  name = "json_fuzzer",
  srcs = ["fuzzer.c"],
  deps = ["//:gpr", "//:grpc", "//test/core/util:grpc_test_util"],
  corpus = "corpus",
  copts = ["-std=c99"],
)

cc_binary(
    name = "json_rewrite",
    srcs = ["json_rewrite.c"],
    deps = ["//:grpc", "//test/core/util:grpc_test_util", "//:gpr", "//test/core/util:gpr_test_util"],
    testonly = 1,
    copts = ['-std=c99']
)

cc_test(
    name = "json_rewrite_test",
    srcs = ["json_rewrite_test.c"],
    deps = ["//:grpc", "//test/core/util:grpc_test_util", "//:gpr", "//test/core/util:gpr_test_util"],
    copts = ['-std=c99'],
    data = ["rewrite_test_input.json", "rewrite_test_output_condensed.json", "rewrite_test_output_indented.json", ":json_stream_error_test"]
)

cc_test(
    name = "json_stream_error_test",
    srcs = ["json_stream_error_test.c"],
    deps = ["//:grpc", "//test/core/util:grpc_test_util", "//:gpr", "//test/core/util:gpr_test_util"],
    copts = ['-std=c99']
)

cc_test(
    name = "json_test",
    srcs = ["json_test.c"],
    deps = ["//:grpc", "//test/core/util:grpc_test_util", "//:gpr", "//test/core/util:gpr_test_util"],
    copts = ['-std=c99']
)
