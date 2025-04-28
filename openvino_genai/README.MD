# OpenVINO Demos

## How to setup

1. Download OpenVINO Sample Code
- https://storage.openvinotoolkit.org/repositories/openvino_genai/packages/2025.1/windows/openvino_genai_windows_2025.1.0.0_x86_64.zip

2. Install all latest drivers here
- NPU Driver: https://www.intel.com/content/www/us/en/download/794734/intel-npu-driver-windows.html
- GPU Driver: https://www.intel.com/content/www/us/en/download/785597/intel-arc-iris-xe-graphics-windows.html

3. Install Python 3.12.x
- https://www.python.org/ftp/python/3.12.9/python-3.12.9-amd64.exe

4. Enable PowerShell for venv
```
Set-ExecutionPolicy -ExecutionPolicy Unrestricted -Scope CurrentUser
```

## How to run the environments:

Install Python 3.12.x, and in PowerShell/Terminal, type the follow in the folder.

Install the packages
```
python -m venv openvino_env
openvino_env\Scripts\activate
pip install  nncf==2.14.1 onnx==1.17.0 optimum-intel==1.22.0
pip install openvino==2025.1 openvino-tokenizers==2025.1 openvino-genai==2025.1
```
Note: Only 2025.1 is validated for this demo.


## How to compress or download a model from HuggingFace

To download and compress a model (CPU/GPU/NPU):
```
optimum-cli export openvino -m TinyLlama/TinyLlama-1.1B-Chat-v1.0 --weight-format int4 --sym --ratio 1.0 --group-size 128 TinyLlama-1.1B-Chat-v1.0
```

To download a pre-compressed model (for CPU/GPU only - NPU please follow the above compression methods):
```
huggingface-cli.exe download OpenVINO/Phi-3-mini-4k-instruct-int4-ov --local-dir Phi-3-mini-4k-instruct-int4-ov
```


## References:
NPU with OpenVINO GenAI: https://docs.openvino.ai/2025/openvino-workflow-generative/inference-with-genai/inference-with-genai-on-npu.html
