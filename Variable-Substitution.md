Variable can be inserted into various fields of project CI spec. Variable substitution happens inside _{}_. Backslash should be used to escape normal occurrences of _{_, _}_, and _\\_. The list of available variables will be prompted when _{_ is typed. Below is some examples (assume project name is _foobar_):

| Original           | Substitued |
|----------          |------------|
|ubuntu-{projectName}| ubuntu-foobar |
|ubuntu-\\{projectName\\}|ubuntu-{projectName}|
|ubuntu-\\\\{projectName}|ubuntu-\\foobar|
