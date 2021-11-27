# The HIST framework for stock trend forecasting
The implementation of the paper "[HIST: A Graph-based Framework for Stock Trend Forecasting via Mining Concept-Oriented Shared Information](https://arxiv.org/abs/2110.13716)".
![image](https://user-images.githubusercontent.com/25242325/139006788-b51b18c2-1bcf-44b8-921a-b10d4b197e91.png)

## Environment
1. Install python3.7, 3.8 or 3.9. 
2. Install the requirements in [requirements.txt](https://github.com/WebConf2022-Submission4/Code/blob/main/requirements.txt).
3. Install the [Qlib](https://github.com/microsoft/qlib) and download the data:
	```
	# install Qlib from source
	pip install --upgrade  cython
	git clone https://github.com/microsoft/qlib.git && cd qlib
	python setup.py install

	# Download the stock features of Alpha360 from Qlib
	python scripts/get_data.py qlib_data --target_dir ~/.qlib/qlib_data/cn_data --region cn --version v2
	```
## Reproduce the stock trend forecasting results
![image](https://user-images.githubusercontent.com/25242325/139006416-c0847b7e-6090-4bd9-9990-567d74198ad0.png)
```
git clone https://github.com/Wentao-Xu/HIST.git
cd HIST
mkdir output
```
### Reproduce our HIST framework
```
# CSI 100
python learn.py --model_name HIST --data_set csi100 --hidden_size 128 --num_layers 2 --outdir ./output/csi100_HIST

# CSI 300
python learn.py --model_name HIST --data_set csi300 --hidden_size 128 --num_layers 2 --outdir ./output/csi300_HIST
```
### Reproduce the baselines
* MLP 
```
# MLP on CSI 100
python learn.py --model_name MLP --data_set csi100 --hidden_size 512 --num_layers 3 --outdir ./output/csi100_MLP

# MLP on CSI 300
python learn.py --model_name MLP --data_set csi300 --hidden_size 512 --num_layers 3 --outdir ./output/csi300_MLP
```

* LSTM
```
# LSTM on CSI 100
python learn.py --model_name LSTM --data_set csi100 --hidden_size 128 --num_layers 2 --outdir ./output/csi100_LSTM

# LSTM on CSI 300
python learn.py --model_name LSTM --data_set csi300 --hidden_size 128 --num_layers 2 --outdir ./output/csi300_LSTM
```

* GRU
```
# GRU on CSI 100
python learn.py --model_name GRU --data_set csi100 --hidden_size 128 --num_layers 2 --outdir ./output/csi100_GRU

# GRU on CSI 300
python learn.py --model_name GRU --data_set csi300 --hidden_size 64 --num_layers 2 --outdir ./output/csi300_GRU
```

* SFM
```
# SFM on CSI 100
python learn.py --model_name SFM --data_set csi100 --hidden_size 64 --num_layers 2 --outdir ./output/csi100_SFM

# SFM on CSI 300
python learn.py --model_name SFM --data_set csi300 --hidden_size 128 --num_layers 2 --outdir ./output/csi300_SFM
```

* GATs
```
# GATs on CSI 100
python learn.py --model_name GATs --data_set csi100 --hidden_size 128 --num_layers 2 --outdir ./output/csi100_GATs

# GATs on CSI 300
python learn.py --model_name GATs --data_set csi300 --hidden_size 64 --num_layers 2 --outdir ./output/csi300_GATs
```

* ALSTM
```
# ALSTM on CSI 100
python learn.py --model_name ALSTM --data_set csi100 --hidden_size 64 --num_layers 2 --outdir ./output/csi100_ALSTM

# ALSTM on CSI 300
python learn.py --model_name ALSTM --data_set csi300 --hidden_size 128 --num_layers 2 --outdir ./output/csi300_ALSTM
```

* Transformer
```
# Transformer on CSI 100
python learn.py --model_name Transformer --data_set csi100 --hidden_size 32 --num_layers 3 --outdir ./output/csi100_Transformer

# Transformer on CSI 300
python learn.py --model_name Transformer --data_set csi300 --hidden_size 32 --num_layers 3 --outdir ./output/csi300_Transformer
```

* ALSTM+TRA 

	We reproduce the ALSTM+TRA with its [source code](https://github.com/microsoft/qlib/tree/main/examples/benchmarks/TRA).
