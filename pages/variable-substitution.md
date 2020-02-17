Variable can be inserted into various fields of project build spec by surrounding with _@_. The list of available variables will be prompted when _@_ is typed. Below is some examples of variable substitutions (assume project name is _foobar_):

| Original           | Substitued |
|----------          |------------|
|ubuntu-@projectName@ (contents enclosed with _@_ is variable and will be substituted)| ubuntu-foobar |
|ubuntu-\\@projectName\\@ (normal occurrences of _@_ should be escaped)|ubuntu-@projectName@|
|ubuntu-\\\\@projectName@ (normal occurrences of backslash should also be escaped)|ubuntu-\\foobar|