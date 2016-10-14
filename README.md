### Description
A small tool to dump Caffe's \*.caffemodel to JSON for inspection (\*.prototxt files is not needed). Will not print all the weights to make the output concise (unless `--data` switch is used).

### Usage
```shell
./caffemodel2json.py CAFFE_ROOT/src/caffe/proto/caffe.proto model_name.caffemodel > dump.json
```
or
```shell
alias caffemodel2json='python2.7 <(curl -sS https://raw.githubusercontent.com/vadimkantorov/caffemodel2json/master/caffemodel2json.py)'
caffemodel2json CAFFE_ROOT/src/caffe/proto/caffe.proto model_name.caffemodel > dump.json
```

Output would be something like:
```
protobuf: calling protoc
protobuf: generated
protobuf: imported
   model: caffemodel read in memory. Deserialization will take a few minutes. Take a coffee!
   model: deserialized
   model: json saved

ALLOK. Quitting
```

### Dependencies
1. Python
2. protobuf (with Python bindings)
3. Caffe's caffe.proto (or from a Caffe's fork, it's important if you are inspecting a model that implements new Caffe layers)

### Credits
The tool reuses a function from https://github.com/dpp-name/protobuf-json. Great thanks to Paul Dovbush for making it available.
