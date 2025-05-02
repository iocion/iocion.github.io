```bash
# 部署deepseek-r1模型
# Pull latest image
# https://hub.docker.com/r/lmsysorg/sglang/tags
docker pull lmsysorg/sglang:latest
# Launch
docker run --gpus all --shm-size 32g -p 30000:30000 -v ~/.cache/huggingface:/root/.cache/huggingface --ipc=host --network=host --privileged lmsysorg/sglang:latest \
    python3 -m sglang.launch_server --model deepseek-ai/DeepSeek-V3 --tp 8 --trust-remote-code --port 30000
```

```bash
```

<span id="busuanzi_container_page_pv">文章总观看量<span id="busuanzi_value_page_pv"></span>次</span>