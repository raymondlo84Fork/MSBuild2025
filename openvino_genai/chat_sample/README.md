# OpenVINO Chat Sample

Follow instructions here to prepare the environment:
https://github.com/raymondlo84Fork/MSBuild2025/blob/main/openvino_genai/README.MD

## How to compress or download a model from HuggingFace

To download and compress a model (CPU/GPU/NPU):
```
optimum-cli export openvino -m TinyLlama/TinyLlama-1.1B-Chat-v1.0 --weight-format int4 --sym --ratio 1.0 --group-size 128 TinyLlama-1.1B-Chat-v1.0
```

To download a pre-compressed model (for CPU/GPU only):
```
huggingface-cli.exe download OpenVINO/Phi-3-mini-4k-instruct-int4-ov --local-dir Phi-3-mini-4k-instruct-int4-ov
```
For NPU usage, please make sure the flags `--sym` and `--group-size 128` are set.

To obtain a meta llama demo, please first get a access token from this link [Access Security Tokens](https://huggingface.co/docs/hub/en/security-tokens), then login with the command line. Additionally, you have to accept to the agreement and wait for the approval (https://huggingface.co/meta-llama). Often this only take a few minutes to an hour.

```
huggingface-cli login
```
Then, you can execute this command. 
```
optimum-cli export openvino --model meta-llama/Llama-3.2-3B-Instruct --task text-generation-with-past --weight-format int4 --group-size -1 --sym --ratio 1.0 llama-3.2-3b-instruct-INT4
```


## How to Run

```
python chat_sample.py TinyLlama-1.1B-Chat-v1.0
```
or replace `TinyLlama-1.1B-Chat-v1.0` with other models such as `Phi-3-mini-4k-instruct-int4-ov` or `Llama-3.2-3B-Instruct`.


## References:
NPU with OpenVINO GenAI: https://docs.openvino.ai/2025/openvino-workflow-generative/inference-with-genai/inference-with-genai-on-npu.html


