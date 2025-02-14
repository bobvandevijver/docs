# merge

`merge(arr2)` is a Twig filter to merge an array with another array:

```twig
{% set values = [1, 2] %}

{% set values = values|merge(['apple', 'orange']) %}

{# values now contains [1, 2, 'apple', 'orange'] #}
```

New values are added at the end of the existing ones.

The `merge` filter also works on hashes:

```twig
{% set items = { 'apple': 'fruit', 'orange': 'fruit', 'peugeot': 'unknown' } %}

{% set items = items|merge({ 'peugeot': 'car', 'renault': 'car' }) %}

{# items now contains { 'apple': 'fruit', 'orange': 'fruit', 'peugeot': 'car', 'renault': 'car' } #}
```

For hashes, the merging process occurs on the keys: if the key does not already exist, it is added but if the key already exists, its value is overridden.

### Tip

If you want to ensure that some values are defined in an array (by given default values), reverse the two elements in the call:

```twig
{% set items = { 'apple': 'fruit', 'orange': 'fruit' } %}

{% set items = { 'apple': 'unknown' }|merge(items) %}

{# items now contains { 'apple': 'fruit', 'orange': 'fruit' } #}
```

### Note

Internally, Twig uses the PHP [array_merge](https://www.php.net/array_merge) function. It supports Traversable objects by transforming those to arrays.

Source: [Twig](https://twig.symfony.com/merge)