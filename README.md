# Backpropagation for Feedforward Networks

A seminar paper with its code, written for the PhD course **Artificial Neural Networks (20.IDI23)**, Doctoral Academic Studies in Computer Science, Faculty of Sciences and Mathematics, University of Niš.
Mentor: Prof. Branimir Todorović · Author: Elvir Muslić

The paper and the notebook are one version: the notebook computes every number, table and figure of the paper and cites the paper's sections, equations and algorithms by their numbers.

## Contents

| File | What it is |
|---|---|
| [`seminar.pdf`](seminar.pdf) | the paper; `seminar.tex` and `seminar.bib` are its LaTeX source |
| [`project/backprop_project.ipynb`](project/backprop_project.ipynb) | the notebook, with its outputs |
| `project/figures/` | the two figures of the paper |
| `project/requirements.txt` | the pinned package versions |

## What the notebook does

- **One step by hand:** the forward pass, the loss and the backward pass of the smallest network, as in Table 1 of the paper.
- **The same gradient two other ways:** PyTorch's automatic differentiation and central differences.
- **XOR:** a 2-4-1 network trained with `torch.nn`, `loss.backward()` and `torch.optim.SGD`.
- **Two moons:** a 2-16-1 network, tested on points it never saw.

## Results

- **By hand:** autograd agrees with the hand gradient to 1.4e-17, central differences to 2.9e-11; one step with step size 1 lowers the loss from 0.089386 to 0.085161.
- **XOR:** the loss falls from 0.1261 to 4.62e-4, and all four inputs are classified correctly.
- **Two moons:** the loss falls from 0.1241 to 0.0017; training and test accuracy are both 1.000.
- **Precision:** all computations are in double precision, with fixed random seeds, so every run gives the same numbers.

## Run

```bash
cd project
python3 -m venv .venv
.venv/bin/pip install -r requirements.txt
.venv/bin/jupyter nbconvert --to notebook --execute --inplace backprop_project.ipynb
```

- The run takes a few seconds and rewrites `project/figures/`.
- Alternatively, open `project/` in VS Code, select the `.venv` kernel and choose Run All.
- To rebuild the paper: `latexmk -pdf seminar.tex` (with biber).

## Credits

- **Theory:** D. E. Rumelhart, G. E. Hinton and R. J. Williams (1986); P. J. Werbos (1990); S. Haykin, *Neural Networks: A Comprehensive Foundation*, 2nd ed., 1998.
- **Software:** PyTorch; scikit-learn (`make_moons`); Matplotlib.
