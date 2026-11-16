# Issue

**Title:** Add layout option to coda plot_boxplots

## Description

**PR Checklist**

* [x] Referenced issue is linked
* [ ] If you've fixed a bug or added code that should be tested, add tests
* [x] Documentation in `docs` is updated

---

## Description of changes

This PR adds a new `layout` parameter to `plot_boxplots()` in the `Sccoda` plotting utilities.

Currently, when `plot_facets=True`, the number of subplot columns is determined using:

```python
col_wrap = int(np.floor(np.sqrt(K)))
```

where `K` is the number of cell types. This tends to produce a **taller ("long") layout** for the facet grid.

The new `layout` parameter allows users to choose between two layouts:

* `"long"` (default): uses `floor(sqrt(K))`, producing a taller layout.
* `"wide"`: uses `ceil(sqrt(K))`, producing a wider layout.

Example usage:

```python
sccoda.plot_boxplots(
    mdata,
    feature_name="condition",
    plot_facets=True,
    layout="wide"
)
```

The default behavior remains unchanged to preserve backward compatibility.

This .

---

## Technical details

When `plot_facets=True`, the column wrapping logic now depends on the `layout` argument:

* `"long"` → `col_wrap = floor(sqrt(K))`
* `"wide"` → `col_wrap = ceil(sqrt(K))`

Validation is added to ensure `layout` is either `"long"` or `"wide"`.

The change only affects the `FacetGrid` layout logic and does not impact any other functionality.

---

## Additional context

This change improves flexibility for users visualizing many cell types, where a wider layout may be preferable for readability.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1ff4cb342ba3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.