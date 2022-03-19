# Buf
Tooling and management for Protobufs

# Problems to solve
1. API designs are inconsistent
2. Dependency management is an afterthought
3. Forwards and backwards compatibility is not enforced
4. Stub distribution is a difficult, unsolved process
5. The tooling ecosystem is limited

Buf builds a modern Protobuf ecosystem
# Buf CLI
The `buf` CLI enables you to create consistent Protobuf APIs that preserve compatibility and comply with best practices. Contains:
- compiler
- linter
- breaking change detector
- generator
# Buf Schema Registry (BSR)
The Buf Schema Registry ([BSR](https://docs.buf.build/bsr/introduction)) is a hosted SaaS platform that serves as your organization’s source of truth for your Protobuf APIs. The BSR enables you to centrally maintain compatibility and manage dependencies, while enabling your clients to consume APIs reliably and efficiently. Similar to `npm` for JavaScript, `pip` for Python, or `cargo` for Rust, the BSR _finally_ brings dependency management to your Protobuf APIs.

# Tour
## Configure and Build
Run `buf mod init` to generate a `buf.yaml` file. The `buf.yaml` file is the root of a Buf module. It is recommended to have the `buf.yaml` file at the root of the proto directory, as that is where all the proto import paths are resolved from. The placement of the `buf.yaml` file is analogous to the `protoc -I` flag, but in Buf there is no include flag. Everything is resolved with the directory that the `buf.yaml` file lives in as the root.

Run `buf build` to build the proto files.

## List Files
Run `buf ls-files` to list all the proto files tracked by the Buf module.

## Lint Files
Run `buf lint` to lint the proto files. You can add lint exceptions by using the `except` clause or ignore specific files by using the `ignore` clause.
```yaml
lint:
  use:
    - DEFAULT
  except:
    - PACKAGE_VERSION_SUFFIX
    - FIELD_LOWER_SNAKE_CASE
    - SERVICE_SUFFIX
  ignore:
	- google/type/datetime.proto
```

You can also run `buf lint --error-format=config-ignore-yaml` to generate the YAML config to ignore specific failures.

## Breaking Changes
Buf is able to detect 4 categories of breaking changes
1. FILE
2. PACKAGE
3. WIRE
4. WIRE_JSON
The recommended value is `FILE`. 

Run `buf breaking --against ../../.git#branch=main,subdir=start/petapis` to run the breaking changes detector against the local main branch.

## Generate Code
Prior to generating code, you'll need to install the [[protoc]] plugins for the language you're trying to generate for.

The `buf.gen.yaml` file configures how `buf generate` executes the protoc plugins. 

### Managed Mode
Configuration option to let Buf set all file options according to an opinionated set of values suitable for each of the supported languages. These options aren't derived from your Protobuf definitions as an API _producer_. Instead, these options relate to how people _consume_ your Protobuf APIs. Different consumers may want different values for these options, especially when a given set of Protobuf definitions is consumed in many different places.

## BSR
[Login](https://buf.build/login)
[Create a token](https://buf.build/settings/user)
CLI login with `buf registry login`
CLI logout with `buf registry logout`

# Push a module
