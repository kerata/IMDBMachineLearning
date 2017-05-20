# Movie Analysis using [IMDB 5000](https://www.kaggle.com/deepmatrix/imdb-5000-movie-dataset) dataset

This project uses ipython notebook which has the JSON structure underneath.
Since this is not in final form and have not designed for display; nb strip approach has been employed.

## Installation of JQ

To install from source code, follow [JQ](https://stedolan.github.io/jq/)

On Ubuntu `sudo apt-get install jq`

On mac using brew `brew install jq`

## Integration with Git

Then change add this to file `./.git/config`

```
[filter "nbstrip_jq"]
clean = "jq --indent 1 \
	'(.cells[] | select(has(\"outputs\")) | .outputs) = []  \
	| (.cells[] | select(has(\"execution_count\")) | .execution_count) = null  \
	| .metadata = {\"language_info\": {\"name\": \"python\", \"pygments_lexer\": \"ipython3\"}} \
	'"
smudge = "cat"
required = true
```

Then finally create this file `./.git/info/attributes` with following intent

```
*.ipynb filter=nbstrip_jq
```

This will clear outputs and execution numbers from the `.ipnb` files before push without changing working directory.

## Project description

// TODO
