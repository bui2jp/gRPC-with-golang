# gRPC with golang

1. https://grpc.io/

    ```
    HTTP/2
    https://grpc.io/docs/languages/go/quickstart/
    golangでgRPCを試す（Dockerを利用)
    ```

2. Docker env
    ```
    docker run --rm --name grpc-test -v $PWD:/root -w /root -it golang:1.14.13 bash
    docker run --rm --name grpc-test -v $PWD:/root -w /root golang:1.14.13 go version
    ```

3. install protobuf-compiler

    ```
    # apt update
    # apt install -y protobuf-compiler

    # protoc --version                                
    libprotoc 3.6.1
    ```

4. Install the protocol compiler plugins for Go

    コンテナの中で実施

    ```
    # export GO111MODULE=on
    # go get google.golang.org/protobuf/cmd/protoc-gen-go \
             google.golang.org/grpc/cmd/protoc-gen-go-grpc

    # export PATH="$PATH:$(go env GOPATH)/bin"
    ```

5. grpc-go/examples/helloworld を実行

    ```
    # git clone -b v1.35.0 https://github.com/grpc/grpc-go
    ```

    server
    ```
    go run greeter_server/main.go
    ```

    client (serverとは別のTerminalで実行)
    ```
    go run greeter_client/main.go
    ```
    server側のterminalでメッセージを確認できる

6. Unary x Streaming

    ストリーミングにも対応しているので試してみる

    ```
    https://grpc.io/docs/what-is-grpc/core-concepts/
    Unary RPC
    Server streaming RPC
    Client streaming RPC
    Bidirectional streaming RPC
    ```

    Web Frontend (Javascript)
    ```
    https://github.com/grpc/grpc-web
    ```