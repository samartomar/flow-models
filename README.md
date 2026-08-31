# flow-models

Model files for [Flow](https://github.com/samartomar/flow), for machines that cannot
reach `huggingface.co`.

Nothing is stored in git — the files are **release assets**, because `model.bin` is well
past GitHub's 100 MB limit for git objects and Git LFS would make every clone pay for it.
Release assets allow 2 GB and are not part of history.

## Use

```bash
gh release download base.en -R samartomar/flow-models -D ~/flow-models/base.en
uv run python -m flow --model ~/flow-models/base.en
```

`--model` pins both decoder tiers to one model: 138 MB instead of 599. Finals are a
little weaker than the usual `small.en` — that tier is what it is for — but everything
else behaves normally.

## What these are

`Systran/faster-whisper-base.en`, snapshot `3d3d5dee26484f91867d81cb899cfcf72b96be6c`,
copied out of a working HuggingFace cache with the symlinks resolved. The cache stores
each file as a symlink into `blobs/`, so a plain copy between machines arrives as four
broken links.
