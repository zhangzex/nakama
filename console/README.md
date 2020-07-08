# Code generation for the Nakama Console

## Generate Swagger documentation

First, create the `console.swagger.json` file using `protoc`.

From within the `console/` directory:
`protoc -I<include-path> --swagger_out=console.swagger.json console.proto`

For example, a sensible set of include paths looks like:

`protoc -I. -I$GOPATH/src/ -I../vendor/github.com/grpc-ecosystem/grpc-gateway -I$GOPATH/src/github.com/grpc-ecosystem/grpc-gateway/third_party/googleapis --swagger_out=. console.proto`

## Generate Go gRPC code

Next, generate the backend Go code to power the console:

`protoc -I. -I$GOPATH/src/ -I../vendor/github.com/grpc-ecosystem/grpc-gateway -I$GOPATH/src/github.com/grpc-ecosystem/grpc-gateway/third_party/googleapis --go_out=plugins=grpc,paths=source_relative:. console.proto`

### Generate Client gRPC code

Lastly, generate client code from the Swagger documentation generated earlier. See the corresponding client SDK for scripts related generating code from a Swagger definition.