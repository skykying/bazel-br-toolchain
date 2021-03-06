package(default_visibility = ["//visibility:public"])

load(":cc_toolchain_config.bzl", "cc_k8_toolchain_config")

cc_toolchain_suite(
    name = "k8-br",
    toolchains = {
        "k8": ":cc_x86_64-toolchain",
    },
)

filegroup(name = "empty")

filegroup(
    name = "all",
    srcs = [
        "@br_toolchain_k8//:all",
        "wrappers/x86_64-buildroot-linux-musl-ar",
        "wrappers/x86_64-linux-cpp.br_real",
        "wrappers/x86_64-linux-gcc-9.1.0.br_real",
        "wrappers/x86_64-linux-ld",
        "wrappers/x86_64-linux-nm",
        "wrappers/x86_64-linux-objdump",
    ],
)

cc_toolchain(
    name = "cc_x86_64-toolchain",
    toolchain_identifier = "x86_64-toolchain",
    toolchain_config = ":x86_64-toolchain-config",
    all_files = ":all",
    compiler_files = ":all",
    dwp_files = ":empty",
    linker_files = ":all",
    objcopy_files = ":all",
    ar_files = ":all",
    strip_files = ":all",
    supports_param_files = False,
)

cc_k8_toolchain_config(
    name = "x86_64-toolchain-config",
)

toolchain(
    name = "linux_x86_64",
    exec_compatible_with = [
        "@platforms//os:linux",
        "@platforms//cpu:x86_64",
    ],
    target_compatible_with = [
        "@platforms//os:linux",
        "@platforms//cpu:x86_64",
    ],
    toolchain = ":cc_x86_64-toolchain",
    toolchain_type = "@bazel_tools//tools/cpp:toolchain_type",
)