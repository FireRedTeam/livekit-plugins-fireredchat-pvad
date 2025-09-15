# FireRedChat pVAD plugin for LiveKit Agents

This plugin provides FireRedChat's open-weight personalized VAD model for LiveKit Agents. 

For speaker embedding update to work properly, please use [our fork of LiveKit Agents](https://github.com/FireRedTeam/FireRedChat) or modify your branch alike to include the ***update_speaker*** call for the first user utterance.

## Installation

```bash
pip install -e .
```

## Download model

```bash
python3 your_agent_worker.py download-files
```
or download directly from [huggingface](
https://huggingface.co/FireRedTeam/fireredchat-pvad)

## Usage

```python
from livekit.plugins import fireredchat_pvad as pvad

def prewarm(proc: JobProcess):
    proc.userdata["vad"] = pvad.VAD.load(activation_threshold=0.5)

# after the first utterance (or when primary speaker switches based on RMS), call VADStream's update_speaker() to update speaker embedding.
```

## License

The plugin source code and model weights are licensed under the Apache-2.0 license.
