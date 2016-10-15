### Description
A small tool to dump Caffe's \*.caffemodel to JSON for inspection (\*.prototxt files is not needed). Will not print all the weights to make the output concise (unless `--data` switch is used). It also supports extracting blobs from \*.binaryproto files (think imagenet_mean.binaryproto).

### Usage

```shell
./caffemodel2json.py CAFFE_ROOT/src/caffe/proto/caffe.proto model_name.caffemodel > dump.json
```
or
```shell
alias caffemodel2json='python2.7 <(curl -sS https://raw.githubusercontent.com/vadimkantorov/caffemodel2json/master/caffemodel2json.py)'
caffemodel2json https://raw.githubusercontent.com/BVLC/caffe/master/src/caffe/proto/caffe.proto model_name.caffemodel > dump.json
```

To dump a binaryproto:
```shell
wget http://dl.caffe.berkeleyvision.org/caffe_ilsvrc12.tar.gz
mkdir -p imagenet_mean && tar -xf caffe_ilsvrc12.tar.gz -C imagenet_mean
./caffemodel2json.py https://raw.githubusercontent.com/BVLC/caffe/master/src/caffe/proto/caffe.proto imagenet_mean/imagenet_mean.binaryproto --data > imagenet_mean.json
```

### Dependencies
1. Python
2. protobuf (with Python bindings)
3. Caffe's caffe.proto (or from a Caffe's fork, it's important if you are inspecting a model that implements new Caffe layers)

### Credits
This tool reuses a function from https://github.com/dpp-name/protobuf-json. Great thanks to Paul Dovbush for making it available.
