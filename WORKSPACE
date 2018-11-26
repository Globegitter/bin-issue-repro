load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")
http_archive(
    name = "build_bazel_rules_nodejs",
    sha256 = "897f609e5d6d6b1a42e2485cb52bea59f2977684a18788e057aa6554f936196f",
    strip_prefix = "rules_nodejs-ee6f2e3ff1d5806ae864d31d28a7daa99057770f",
    url = "https://github.com/bazelbuild/rules_nodejs/archive/ee6f2e3ff1d5806ae864d31d28a7daa99057770f.tar.gz",
)

load("@build_bazel_rules_nodejs//:package.bzl", "rules_nodejs_dependencies")

rules_nodejs_dependencies()

load("@build_bazel_rules_nodejs//:defs.bzl", "node_repositories")

# NOTE: this rule installs nodejs, npm, and yarn, but does NOT install
# your npm dependencies into your node_modules folder.
# You must still run the package manager to do this.
node_repositories(
    node_version = "10.3.0",
    package_json = [
        "//:package.json",
    ],
    preserve_symlinks = True,
    yarn_repositories = {
        "1.9.2": ("yarn-v1.9.2.tar.gz", "yarn-v1.9.2", "3ad69cc7f68159a562c676e21998eb21b44138cae7e8fe0749a7d620cf940204"),
    },
    yarn_urls = ["https://github.com/yarnpkg/yarn/releases/download/v{version}/{filename}"],
    yarn_version = "1.9.2",
)

load("@build_bazel_rules_nodejs//:defs.bzl", "yarn_install")


yarn_install(
    name = "myyarn",
    package_json = "//:package.json",
    yarn_lock = "//:yarn.lock",
)