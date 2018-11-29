# Jupyter Notebook Cheat Sheet

### Suppress token
```bash
--NotebookApp.token=''
```
Using the switch with `docker run`
```bash
docker run -it --rm -p 8888:8888 jupyter/datascience-notebook start.sh jupyter lab --NotebookApp.token=''
```
#### Docker Compose
```yaml
command:
     "start.sh jupyter lab --NotebookApp.token=''"
```

### Align image
```html
<img style="float: none; display: inline;" src="/path/to/image.png"/>
```
[Forcing images to not wrap](https://stackoverflow.com/a/3010853/6146580)
