# flow-models

Model files for [Flow](https://github.com/samartomar/flow), mirrored for machines that
cannot reach `huggingface.co`.

Nothing is stored in git — the files are **release assets**, because `model.bin` is well
past GitHub's 100 MB limit for git objects and Git LFS would make every clone pay for it.
Release assets allow 2 GB and are not part of history.

## Use

```bash
curl -L -O https://github.com/samartomar/flow-models/releases/download/base.en/config.json
curl -L -O https://github.com/samartomar/flow-models/releases/download/base.en/model.bin
curl -L -O https://github.com/samartomar/flow-models/releases/download/base.en/tokenizer.json
curl -L -O https://github.com/samartomar/flow-models/releases/download/base.en/vocabulary.txt

uv run python -m flow --model /path/to/that/directory
```

`--model` pins both of Flow's decoder tiers to one model: 138 MB instead of 599. Finals
are a little weaker than the `small.en` that tier normally uses — that is what the split
is for — but everything else behaves normally.

`gh release download base.en -R samartomar/flow-models -D <dir>` does the same thing in
one line where the GitHub CLI is available and permitted.

## What these are, and whose they are

`Systran/faster-whisper-base.en`, snapshot `3d3d5dee26484f91867d81cb899cfcf72b96be6c`,
copied out of a working HuggingFace cache with the symlinks resolved. The cache stores
each file as a symlink into `blobs/`, so a plain copy between machines arrives as four
broken links — which is the whole reason this mirror exists in this shape.

**These are not my weights.** They are redistributed unmodified from
[Systran/faster-whisper-base.en](https://huggingface.co/Systran/faster-whisper-base.en),
which is published under the **MIT licence**. The upstream model card is the source of
truth for provenance, training data and intended use; nothing here alters the files or
adds a claim about them. If you can reach HuggingFace, take them from there instead —
this exists only for networks that cannot.
