[[_intro quick start docker]]



# Jupyter Lab For Data Science


```bash
docker run -it --name jupter-data1 -p 8888:8888 -v ${PWD}:/home/jovyan/work -e JUPYTER_ENABLE_LAB=yes jupyter/datascience-notebook


docker start -ia jupyter-data1
docker rm jupyter-data1
```

`-e JUPYTER_ENABLE_LAB=yes` jupyter will start with lab interface otherwise with the notebook interface










