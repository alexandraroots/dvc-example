Настраиваем dvc
```
conda create --name dvc python=3.11 -y
conda activate dvc
pip install dvc
```

Активируем dvc
```
dvc init
```

Скачиваем датасет iris для примера
```
wget -P data/ https://raw.githubusercontent.com/uiuc-cse/data-fa14/gh-pages/data/iris.csv
```

```
dvc add data/iris.csv
```

Настариваем удаленное хранилище для файлов
```
pip install dvc-gdrive
dvc remote add myremote gdrive://<grive-url>
```

```
dvc push
dvc pull
```

Добавляем stage предобработки в dug
```
dvc stage add -n prepare -d transform.py -d data/iris.csv -o data/prepared python transform.py
dvc repro
dvc dag
```

Добавляем stage обучения в dug
```
dvc stage add -n train -d train.py -d data -o data/model.joblib -M metrics.csv python train.py
```