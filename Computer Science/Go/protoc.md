When executing the protoc command, you have to specify all the directories where the imported protos live.

Example: `protoc -I=. -I=$GOPATH/pkg/mod/github.com/regen-network/protobuf@v1.3.3-alpha.regen.1/gogoproto --go_out=. *.proto`

This is annoying to do, so Osmosis and Cosmos SDK wrote a shell script that automatically finds the directory locations of imported proto files and runs protoc with that list. See [protocgen.sh](https://github.com/osmosis-labs/osmosis/blob/f89750244b266cd129dfc53b48a240703384f4e2/scripts/protocgen.sh) for more details.

# Go
The Cosmos SDK uses https://github.com/gogo/protobuf, which is no longer being actively maintained. The official golang protobuf support is at https://github.com/golang/protobuf, which has been superseded by https://pkg.go.dev/google.golang.org/protobuf.

