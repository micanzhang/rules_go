load("//go:def.bzl", "go_library", "go_test")

config_setting(
    name = "linux_amd64",
    values = {"cpu": "k8"},
)

config_setting(
    name = "darwin_amd64",
    values = {"cpu": "darwin"},
)

LIB_AMD64_SRCS = [
    "foo_amd64.go",
    "foo_amd64.s",
    "foo_amd64.h",
]

LIB_OTHER_SRCS = ["foo_other.go"]

go_library(
    name = "go_default_library",
    srcs = select({
        ":linux_amd64": LIB_AMD64_SRCS,
        ":darwin_amd64": LIB_AMD64_SRCS,
        "//conditions:default": LIB_OTHER_SRCS,
    }),
)

go_test(
    name = "go_default_test",
    srcs = ["foo_test.go"],
    library = ":go_default_library",
)
