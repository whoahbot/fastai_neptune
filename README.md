# Neptune.ai
> Integration with <a href='https://www.neptune.ai'>neptune.ai</a>.


## Install

`pip install fastai_neptune`

## Registration
1. Create **free** account: [neptune.ai/register](https://neptune.ai/register).
2. Export API token to the environment variable (more help [here](https://docs.neptune.ai/python-api/tutorials/get-started.html#copy-api-token)). In your terminal run:

```
export NEPTUNE_API_TOKEN='YOUR_LONG_API_TOKEN'
```

or append the command above to your `~/.bashrc` or `~/.bash_profile` files (**recommended**). More help is [here](https://docs.neptune.ai/python-api/tutorials/get-started.html#copy-api-token).

## Installation
1. You need to install neptune-client. In your terminal run:

```
pip install neptune-client
```

or (alternative installation using conda). In your terminal run:

```
conda install neptune-client -c conda-forge
```
2. Install [psutil](https://psutil.readthedocs.io/en/latest/) to see hardware monitoring charts:

```
pip install psutil
```

## How to use

Key is to call `neptune.init()` before you create `cnn_learner()`. A new experiment will be created before model fitting.

Use `NeptuneCallback` in your `Learner`, like this:

```
from fastai.callback.neptune import NeptuneCallback

neptune.init('USERNAME/PROJECT_NAME')  # specify your project here

learn = cnn_learner(dls, resnet18, metrics=error_rate, cbs=NeptuneCallback())
learn.fit_one_cycle(1)
```

