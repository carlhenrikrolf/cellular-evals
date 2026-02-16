# Datasets

How to format the datasets

## Samples

How to format the samples.
More information on how they are parsed within Inpect AI in the next section.

### Inspect AI

See [here](https://inspect.aisi.org.uk/datasets.html)

**Data structures.**
The data structures that can be used for the various fields below.

`str`, `list`, `None`, `dict`, `tuple`.
Standard Python types.

`Content`.
Not sure what this is.
Could be used to add paths to external files.

`ChatMessage`.
Via `from inspect_ai.model import ChatMessage`.
In `.json`, `ChatMessage` is represented as a dictionary with two fields:
- `role` is either `"system"`, `"user"`, `"assistant"`, or `"tool"`.
I am not sure how standardized this is, maybe you can add your own?
- `content` is either a `str` or a `list` of `Content`.

**Fields.**
These are the available fields in the `.json` file.
Non-mandatory fields may be set to `None`.

`input`.
A `str` or a `list` of `ChatMessage`s.
The only mandatory field.

`choices`.
A `list`of `str`s.
Multiple.choice anser list

`target`.
A `str` or `list` of `str`s.
The ideal output from the answer.
Can be a number or a more fluid text description.

`id`.
A `str` and unique identifier for the sample.
If not specified, will be automatically incremented.

`metadata`.
A `dict` of arbitrary structure.

`sandbox`.
A `str` for the type or a `tuple` for type and config file (path or content?).

`files`
A `dict` of `str` with files that should go with the sample. (Paths?)

`setup`.
A `str` for a setup script that runs at init for sample within the default environment.


___


If only input and target are used, you can save as a csv and load directly with `csv_dataset(<x>)`.


### Hugging Face

## Parser

### Solver

See [here](https://inspect.aisi.org.uk/solvers.html).

**Data structures.**
Additional data structures used for the solver.

`Solver`.
Via `from inspect_ai.solver import <x>` where `<x>` is a specific solver.
- `generate()`. Default if nothing specified. Not strictly necessary.
- `system_message(<x>)` where `<x>` is a `str`.
That `str` is shown to the solver but not the scorer.
It can be parametrized with `<x>.format()`.
- `user_message(<x>)`.
`str` `<x>` appended to list of messages with `role="user"`.
- `chain_of_thought()` is standard CoT template.
- `use_tools()`
- `self_critique(model=<x>)`.
By default the model is the same.
- `multiple_choice()`

**Arguments.**
These are arguments to the `Task` class via `from inpect_ai import Task`.

`dataset`.
An Inspect AI dataset is imported straightforwardly.

`solver`
`list`of `Solver`s

`scorer`.
**TODO**

**Additional options.**

- `setup`
- `cleanup`
- `metrics`
- `model`
- `config`[^config]
- `model_roles`
- `sandbox`
- `approval`
- `epochs`
- `fail_on_error`

[^config]: GenerateConfig = GenerateConfig(max_retries=None, timeout=None, attempt_timeout=None, max_connections=None, system_message=None, max_tokens=None, top_p=None, temperature=None, stop_seqs=None, best_of=None, frequency_penalty=None, presence_penalty=None, logit_bias=None, seed=None, top_k=None, num_choices=None, logprobs=None, top_logprobs=None, parallel_tool_calls=None, internal_tools=None, max_tool_output=None, cache_prompt=None, verbosity=None, effort=None, reasoning_effort=None, reasoning_tokens=None, reasoning_summary=None, reasoning_history=None, response_schema=None, extra_body=None, cache=None, batch=None)


### Scorer

See [here](https://inspect.aisi.org.uk/scorers.html).
Exist both CORRECT and INCORRECT scores as well as scores that exist on a continuum.
**TODO: check whether scores are between 0 and or arbitrary.** 
Seems to be able to be multi-dimensional as well.


## Multiple Choice

A bit more complicated.
**TODO**