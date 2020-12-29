---
name: Bug report
about: Scanpy doesn’t do what it should? Please help us fix it!
title: ''
labels: bug
assignees: ''
---

- [ ] I have checked that this issue has not already been reported.
- [ ] I have confirmed this bug exists on the latest version of scanpy.
- [ ] (optional) I have confirmed this bug exists on the master branch of scanpy.

---

**Note**: Please read [this guide](https://matthewrocklin.com/blog/work/2018/02/28/minimal-bug-reports) detailing how to provide the necessary information for us to reproduce your bug.


### Minimal code sample (that we can copy&paste without having any data)

```python
sc.pp.highly_variable_genes(adata, flavor='cell_ranger', n_top_genes=4000)
print('\n','Number of highly variable genes: {:d}'.format(np.sum(adata.var['highly_variable'])))
```

```pytb
ValueError                                Traceback (most recent call last)
<ipython-input-46-616fc10e63ff> in <module>
----> 1 sc.pp.highly_variable_genes(adata, flavor='cell_ranger', n_top_genes=4000)
      2 print('\n','Number of highly variable genes: {:d}'.format(np.sum(adata.var['highly_variable'])))

~\anaconda3\lib\site-packages\scanpy\preprocessing\_highly_variable_genes.py in highly_variable_genes(adata, layer, n_top_genes, min_disp, max_disp, min_mean, max_mean, span, n_bins, flavor, subset, inplace, batch_key)
    424 
    425     if batch_key is None:
--> 426         df = _highly_variable_genes_single_batch(
    427             adata,
    428             layer=layer,

~\anaconda3\lib\site-packages\scanpy\preprocessing\_highly_variable_genes.py in _highly_variable_genes_single_batch(adata, layer, min_disp, max_disp, min_mean, max_mean, n_top_genes, n_bins, flavor)
    242         from statsmodels import robust
    243 
--> 244         df['mean_bin'] = pd.cut(
    245             df['means'],
    246             np.r_[-np.inf, np.percentile(df['means'], np.arange(10, 105, 5)), np.inf],

~\anaconda3\lib\site-packages\pandas\core\reshape\tile.py in cut(x, bins, right, labels, retbins, precision, include_lowest, duplicates, ordered)
    273             raise ValueError("bins must increase monotonically.")
    274 
--> 275     fac, bins = _bins_to_cuts(
    276         x,
    277         bins,

~\anaconda3\lib\site-packages\pandas\core\reshape\tile.py in _bins_to_cuts(x, bins, right, labels, precision, include_lowest, dtype, duplicates, ordered)
    399     if len(unique_bins) < len(bins) and len(bins) != 2:
    400         if duplicates == "raise":
--> 401             raise ValueError(
    402                 f"Bin edges must be unique: {repr(bins)}.\n"
    403                 f"You can drop duplicate edges by setting the 'duplicates' kwarg"
    
    
    
    ValueError: Bin edges must be unique: array([          -inf, 1.00000000e-12, 1.00000000e-12, 1.00000000e-12,
       1.00000000e-12, 1.00000000e-12, 1.00000000e-12, 1.00000000e-12,
       1.00000000e-12, 1.11241045e-04, 2.44672419e-04, 5.69339462e-04,
       1.35840576e-03, 3.49938189e-03, 1.02259867e-02, 2.97723795e-02,
       7.22420720e-02, 1.46845240e-01, 2.97005969e-01, 3.42389128e+00,
                  inf]).
You can drop duplicate edges by setting the 'duplicates' kwarg

```

#### Versions

<details>

[Paste the output of scanpy.logging.print_versions() leaving a blank line after the details tag]

</details>
