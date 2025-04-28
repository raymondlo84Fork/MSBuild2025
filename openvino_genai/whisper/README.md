# OpenVINO Whisper Sample

Follow instructions here to prepare the environment:
https://github.com/raymondlo84Fork/MSBuild2025/blob/main/openvino_genai/README.md

```
#Make sure you activate the environment after restarting the terminal
./openvino_venv/Script/bin
```
## Download the model

First we download and export the whisper model from huggingface for CPU or GPU. 
```
optimum-cli export openvino --trust-remote-code --model openai/whisper-base whisper-base
```
If NPU is the inference device, an additional option --disable-stateful is required. See NPU with OpenVINO GenAI for the detail.

```
optimum-cli export openvino --trust-remote-code --model openai/whisper-base whisper-base-npu --disable-stateful
```
