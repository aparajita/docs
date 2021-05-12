---
id: onBoundVariableChange
title: On Bound Variable Change
---

| Code | Can be called by | 定義                                          |
| ---- | ---------------- | ------------------------------------------- |
| 54   | フォーム             | The variable bound to a subform is modified |


## 説明

This event is generated in the context of the form method of a [subform](FormObjects/subform_overview.md) as soon as a value is assigned to the variable bound with the subform in the parent form (even if the same value is reassigned) and if the subform belongs to the current form page or to page 0.

Form more information, refer to the [Managing the bound variable](FormObjects/subform_overview.md#managing-the-bound-variable) section.