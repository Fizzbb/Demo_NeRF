## An Implementation of NeRF

NeRF (Neural Radiance Fields) is a method for synthesizing novel views of complex scenes. 

### Installation
```angular2html
git clone https://github.com/YHDING23/Demo_NeRF.git
cd demo_nerf
mkdir venv_nerf
virtualenv -p python3.6 venv_nerf
source venv/bin/activate

pip install -r requirements.txt
```

### Quick Start
Download data fro two example datasets: `lego` and `fern`.
```angular2html
bash download_example_data.sh
```
It downloads data to the `data/` folder, and two types of datasets (llff_data and synthetic) are placed seperately:
```angular2html
├── configs                                                                                                       
│   ├── ...                                                                                      
├── data                                                                                                                                                                                                       
│   ├── nerf_llff_data                                                                                                  
│   │   └── fern
│   │   └── ... 
|   ├── nerf_synthetic
|   |   └── lego
│   │   └── ...
```
To train NeRF on different datasets:
```angular2html
python run_nerf.py --config configs/{DATASET}.txt
```

For example, train a `lego` NeRF:
```angular2html
python run_nerf.py --config configs/lego.txt
```

To test NeRF trained on different datast:
```angular2html
python run_nerf.py --config configs/{DATASET}.txt --render_only
```
The training requests <=4G GPU memory. After training for `fern` 200k iterations (~5.5 hours on a single RTX2080), you can find the video at `logs/fern_test/fern_test_spiral_200000_rgb.mp4` and `logs/fern_test/fern_test_spiral_200000_disp.mp4`. 
