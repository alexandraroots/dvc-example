
```
conda create --name dvc python=3.11 -y
conda activate dvc
pip install dvc
```

```
dvc init
```

```
wget -P data/ https://raw.githubusercontent.com/uiuc-cse/data-fa14/gh-pages/data/iris.csv
```

```
dvc add data/iris.csv
```

```
pip install dvc-gdrive
dvc remote add myremote gdrive://<grive-url>
```

```
dvc push
dvc pull
```

```
dvc stage add -n prepare -d transform.py -d data/iris.csv -o data/prepared python transform.py
dvc repro
dvc dag
```

```
dvc stage add -n train -d train.py -d data -o data/model.joblib -M metrics.csv python train.py
```