# BNU-Exam-Dataset & EduOCR

Official repository on "**Bridging the Gap in Exam Handwritten Text Recognition: Dataset, Benchmark, and Modeling**", including:
- **BNU-Exam-HTR** – a large-scale HTR dataset from real exam papers.
- **BNU-Exam-Benchmark** – a fine-grained evaluation benchmark with 12 real exam writing scenarios.
- **EduOCR** – an exam-oriented OCR method.

<div style="display: flex; justify-content: space-between;">
  <img src="Pasted image 20251107050834.png" alt="Image 1" style="width: 40%; height: auto;">
  <img src="Pasted image 20251107050622.png" alt="Image 2" style="width: 25%; height: auto;">
  <img src="Pasted image 20251107050648.png" alt="Image 3" style="width: 25%; height: auto;">
</div>

---
# Download Exam-Scene Dataset

## Trainning Set
| Language | Dataset         |   Size | Language | Dataset           | Size  |
| -------- | --------------- | ------:| -------- | ----------------- | ----- |
| English  | BNU-Exam-HTR-EN |    27K | Chinese  | BNU-Exam-HTR-ZH   | 264K  |
|          | TAL-OCR-ENG     |    10K |          | CASIA-HWDB2.x     | 52.2K |
|          | GNHK (line)     |   4.6K |          | TAL-OCR-CHN-train | 10.4K |
|          | GNHK (word)     |  31.2K |          | SCUT-EPT-train    | 40K   |
|          | IAM             |   6.5K |          | BCTR-hw (train)   | 74.6K |
|          | IMGUR5K (word)  | 157.9K |          | BCTR-hw (val)     | 18.6K |
|          | Synthetic data  |    60K |          | Synthetic data    | 60K   |
|          | Total      |   296K |          | Total       | 520K  |


+ For the **SCUT-EPT** and **BCTR-hw (SCUT-HCCDoc)**, please first downloaded at [SCUT-EPT](https://github.com/HCIILAB/SCUT-EPT_Dataset_Release) and [SCUT-HCCDoc](https://github.com/HCIILAB/SCUT-HCCDoc_Dataset_Release). Then divide **SCUT-HCCDoc** into training/validation/testing set following [BCTR-hw setting](https://github.com/FudanVI/benchmarking-chinese-text-recognition?tab=readme-ov-file).
+ Other trainning datasets are available in xxx. 

In the end, The trainning set is organized in the following directory format:
```
├── zh_train
    ├── bnu-exam-htr-zh
    │   ├── data.mdb
    │   │── lock.mdb
    ├── CAISA-HWDB2x
    ├── SCUT-EPT_train
	├── TAL_OCR_CHN_train
	├── bctr_hw
	├── syn_comp
	├── syn_supp
    └── syn_swit
├── EN_train
    ├── bnu-exam-htr-zh
    │   ├── data.mdb
    │   │── lock.mdb
    ├── GNHK_train_line_processed
    ├── GNHK_train_word_processed
	├── IAM_train
	├── TAL_OCR_ENG
	├── imgur5k_train
	├── syn_comp
	├── syn_supp
    └── syn_swit
```

## BNU-Exam-Benchmark

| Challenge Type                      | English | Chinese |
|-------------------------------------|:-------:|:-------:|
| --- 11 Common Challenges ---        |         |         |
| common                              |   6723  |   1403  |
| long                                |   1256  |   1121  |
| ultra long                          |   1414  |   1046  |
| illegible                           |   1663  |   1098  |
| hard erasure                        |   1256  |   1289  |
| soft erasure                        |   1263  |   1196  |
| supplement                          |   1004  |   1084  |
| switching                           |   507   |   380   |
| replacement                         |   1073  |   1147  |
| Compressed Text at Line End         |   1039  |   354   |
| multi-type                          |   1073  |   1057  |
| --- Language-Specific Challenge --- |         |         |
| unspaced (EN-specific)              |   887   |    --   |
| wrong (ZH-specific)                 |    --   |   1010  |
| Total                               |  19173  |  12185  |

+ BNU-Exam-Benchmark is available in xxx. Directory format:
```
├── bnu_zh_benchmark
    ├── common_0
    │   ├── data.mdb
    │   │── lock.mdb
    ├── LongText_1
    ├── UltraLongText_2
	...
	└── complexText_11
├── bnu_en_benchmark
    ├── common_0
    │   ├── data.mdb
    │   │── lock.mdb
    ├── LongText_1
    ├── UltraLongText_2
	...
	└── complexText_11
```

---
# EduOCR
## Installation
```
git clone https://github.com/BNU-ERC-ITEA/BNU-Exam-HTR
conda create -n eduocr_env python=3.8
conda activate eduocr_env
pip install -r requirements.txt
```

## checkpoint

Our model checkpoint is available at [xxx]()。

## Evaluation

```python
# On bnu_en_benchmark
CUDA_VISIBLE_DEVICES=0 torchrun --nproc_per_node=1 --master-port=25071 tools/eval_rec_all_bnu_en_benchmark_lmdb.py --c configs_bnu_en/eduocr/eduocr.yml

# On bnu_zh_benchmark
CUDA_VISIBLE_DEVICES=0 torchrun --nproc_per_node=1 --master-port=25071 tools/eval_rec_all_bnu_zh_benchmark_lmdb.py --c configs_bnu_zh/eduocr/eduocr.yml
```


## Acknowledgments

+ Thank all collaborators who helped with the collection and annotation of this dataset and benchmark!
+ EduOCR is built based on the [PaddleOCR](https://github.com/PaddlePaddle/PaddleOCR), [PytorchOCR](https://github.com/WenmuZhou/PytorchOCR), [OpenOCR](https://github.com/Topdu/OpenOCR/tree/main) and [MMOCR](https://github.com/open-mmlab/mmocr). We sincerely appreciate their awesome work!

## Citation

```

```
