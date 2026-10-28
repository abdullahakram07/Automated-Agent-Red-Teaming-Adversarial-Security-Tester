# Development

Use Python 3.12 or later. Keep probe prompts synthetic, avoid collecting generated answers, and use an explicitly allowlisted local mock target for development. The runner currently supports plain-text OpenAI-compatible chat messages and a small set of operator-authored regex outcomes.

Suggested contributor checks:

```sh
python -m compileall -q app
python -m pytest
```

Add tests for malformed campaigns, disallowed hosts, invalid patterns, target errors, response-size limits, multi-turn transcript ordering, and report redaction before extending the runner. These commands describe the intended workflow; validation status is reported separately for each change.
