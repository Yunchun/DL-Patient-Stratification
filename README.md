# CS598 Final Project - Deep Representation Learning 



## Dependencies

Install the dependencies by running: 

```shell
$ pip install -r requirements.txt
```

Python 3.6+ is recommended for this project. 



## Data Download Instructions

We already put the preprossed Reddit post data under the `data_example` folder. EHR synthetic data can be found under the `data_example` folder in the original repo. 



## Train and Evaluate

Model parameters can be modified in `utils.py`. 

can be found in `data_example` folder. 
Outputs will be stored in `./data_example/encodings` and include ConvAE latent representations, 
To train the model:

```bash
$ python -u ./patient_representations.py ./data_example/ 
```

To test the trained models, we can set `--test-set` to True:

```bash
$ python -u ./patient_representations.py ./data_example/ --test_set True
```

## Data 

Suicide data include: 

> 500 patients, 70:30 split for train and test 
>
> vocabulary size = 22928;

Synthetic data include:
> 200 patients, 50:50 split for train and test;
>
> vocabulary size = 200;



## Table of Results

Performance on synthetic EHR data: 

|                | ConvAe with 1-layer CNN | ConvAe with 2-layer CNN |
| -------------- | ----------------------- | ----------------------- |
| Train Accuracy | 0.131                   | 0.132                   |
| Train Loss     | 4.083                   | 4.087                   |
| Test Accuracy  | 0.135                   | 0.137                   |
| Test Loss      | 5.580                   | 5.604                   |

Accuracy here doesn't imply much about the model as it is a unsupervised learning task without ground truth labels.  

| Silhouette Score  | RawCount | ConvAE(1-layer) | ConAE(2-layer) |
| ----------------- | -------- | --------------- | -------------- |
| k=2 means cluster | 0.0782   | 0.6171          | 0.6804         |
| k=5 means cluster | 0.0879   | 0.0923          | 0.5894         |

Performance on social media data to assess suicide risk: 

|         | RawCount | ConvAE(1-layer) | ConAE(2-layer) |
| ------- | -------- | --------------- | -------------- |
| Entropy | 0.0437   | 0.0182          | 0.0384         |
| Purity  | 0.5457   | 0.6200          | 0.84           |



## Citation to the Original Paper
Landi, I., Glicksberg, B. S., Lee, H. C., Cherng, S., Landi, G., Danieletto, M., Dudley, J. T., Furlanello, C., & Miotto, R. Deep representation learning of electronic health records to unlock patient stratification at scale. npj Digit. Med. 3, 96 (2020). https://doi.org/10.1038/s41746-020-0301-zDeep

The original repo can be found in [this link](https://github.com/landiisotta/convae_architecture).



