# RobustKV: Defending Large Language Models against Jailbreak Attacks via KV Eviction

## Overview  
**RobustKV** is a lightweight, plug-and-play defense layer for transformer-based LLMs that leverages **KV eviction** to thwart jailbreak attacks (e.g., AutoDAN). By tracking and ranking key–value entries in self-attention memory and evicting the most “suspicious” ones at inference time, RobustKV dramatically reduces malicious instruction leakage while preserving benign performance.


## Environment Setup
**RobustKV** uses the same environment as [SnapKV](https://github.com/FasterDecoding/SnapKV) so you can either set up through their repository or follow:
```bash
transformers==4.37.0 and flash-attn==2.4.0 
```


## Usage 
### 1. **Baseline AutoDAN Evaluation**  
Evaluate the default AutoDAN jailbreak on Llama2-chat-7b:
   ```bash
   python autodan_hga_eval.py
   ```

### 2. **RobustKV Defense**
Run the same attack with RobustKV enabled:

  ```bash
  python RobustKV-AutoDAN.py
  ```

## Features  
- **Selective KV Eviction**  
  - Monitors attention KV stores during inference  
  - Scores entries by attack potential  
  - Evicts top-ranked entries to block harmful prompts  
- **Seamless Integration**  
  - Built on the same low-level KV Optimization Application such as [SnapKV](https://github.com/FasterDecoding/SnapKV)  
  - Minimal code changes—drop-in wrapper around any HuggingFace transformer  
- **Configurable & Extensible**  
  - Adjustable eviction thresholds per experiment  
  - Custom scoring functions can be plugged in  



