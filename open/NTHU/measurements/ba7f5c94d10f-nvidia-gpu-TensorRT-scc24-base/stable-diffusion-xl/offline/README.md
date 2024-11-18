This experiment is generated using the [MLCommons Collective Mind automation framework (CM)](https://github.com/mlcommons/cm4mlops).

*Check [CM MLPerf docs](https://docs.mlcommons.org/inference) for more details.*

## Host platform

* OS version: Linux-6.8.0-47-generic-x86_64-with-glibc2.35
* CPU version: x86_64
* Python version: 3.10.12 (main, Sep 11 2024, 15:47:36) [GCC 11.4.0]
* MLCommons CM version: 3.4.1

## CM Run Command

See [CM installation guide](https://docs.mlcommons.org/inference/install/).

```bash
pip install -U cmind

cm rm cache -f

cm pull repo Catking14@cm4mlops --checkout=4d692d3bc4ac035395b6f5ef7379d4e486cf17ec

cm run script \
	--tags=run-mlperf,inference,_r4.1,_short,_scc24-base \
	--model=sdxl \
	--implementation=nvidia \
	--framework=tensorrt \
	--category=datacenter \
	--scenario=Offline \
	--execution_mode=test \
	--env.CM_NVIDIA_MLPERF_SCRATCH_PATH=/home/cmuser/cm-mlperf-fp8 \
	--env.CM_MLPERF_INFERENCE_TEST_QPS=5 \
	--device=cuda \
	--division=open \
	--quiet \
	--target_qps=5 \
	--offline_target_qps=5 \
	--use_graphs \
	--env.CM_NVIDIA_NUM_GPUS=4 \
	--env.CM_SKIP_MODEL_DOWNLOAD=yes \
	--env.CM_SKIP_PREPROCESS_DATASET=yes \
	--env.LD_LIBRARY_PATH=/opt/hpcx/ucx/lib:/opt/hpcx/ucc/lib:/usr/local/lib/python3.10/dist-packages/torch/lib:/usr/local/lib/python3.10/dist-packages/torch_tensorrt/lib:/usr/local/cuda/compat/lib:/usr/local/nvidia/lib:/usr/local/nvidia/lib64 \
	--env.CM_SKIP_NVMITTEN=yes \
	--test_query_count=5000 \
	--clean
```
*Note that if you want to use the [latest automation recipes](https://docs.mlcommons.org/inference) for MLPerf (CM scripts),
 you should simply reload Catking14@cm4mlops without checkout and clean CM cache as follows:*

```bash
cm rm repo Catking14@cm4mlops
cm pull repo Catking14@cm4mlops
cm rm cache -f

```

## Results

Platform: ba7f5c94d10f-nvidia-gpu-TensorRT-scc24-base

Model Precision: int8

### Accuracy Results 
`CLIP_SCORE`: `31.23426`, Required accuracy for closed division `>= 31.68632` and `<= 31.81332`
`FID_SCORE`: `23.67816`, Required accuracy for closed division `>= 23.01086` and `<= 23.95008`

### Performance Results 
`Samples per second`: `4.23403`
