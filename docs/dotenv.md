# .env

The .env file should contain two parts: experiment settings and API keys.
Why not to share the API keys should be obvious.
The experiment settings are changed for different experiments and are in any case saved in the logs, so there is no reason to keep them in a repository either.

**Experiment settings.**
- `INSPECT_EVAL_MODEL` is the name of the company followed by the name of the model.[^ModelExamples]
- `INSPECT_EVAL_LIMIT` is the number of samples.
- `INSPECT_EVAL_EPOCHS` is the number of epochs, i.e. repeats of each sample.
- `INSPECT_EVAL_MAX_CONNECTIONS` is the maximum number of concurrent connections to the model provider.

More options are available at [AISI](https://inspect.aisi.org.uk/options.html).

**API keys.**
- `<PROVIDER>_API_KEY` is the api key.
- `<PROVIDER>_BASE_URL`is a usually optional base url
- `HF_TOKEN` is an api key for dowloading and running a model locally from Hugging Face.
 
More options are available at [AISI](https://inspect.aisi.org.uk/providers.html).

[^ModelExamples]: Examples of models include `INSPECT_EVAL_MODEL=anthropic/claude-haiku-3-0
INSPECT_EVAL_MODEL=azureai/Llama-3.3-70B-Instruct
INSPECT_EVAL_MODEL=fireworks/accounts/fireworks/models/deepseek-r1-0528
INSPECT_EVAL_MODEL=google/gemini-2.0-flash-lite
INSPECT_EVAL_MODEL=grok/grok-3-mini
INSPECT_EVAL_MODEL=groq/llama-3.1-70b-versatile
INSPECT_EVAL_MODEL=hf/meta-llama/Llama-2-13b-chat-hf
INSPECT_EVAL_MODEL=hf/openai-community/gpt2
INSPECT_EVAL_MODEL=hf-inference-providers/openai/gpt-oss-120b:cerebras
INSPECT_EVAL_MODEL=mistral/mistral-large-2512
INSPECT_EVAL_MODEL=openai/gpt-5-nano
INSPECT_EVAL_MODEL=perplexity/sonar
INPECT_EVAL_MODEL=together/meta-llama/Meta-Llama-3.1-70B-Instruct-Turbo`