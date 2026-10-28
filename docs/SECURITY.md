# Security and responsible use

- Use only systems for which the operator has explicit written authorization and a defined test scope.
- Keep the API on localhost unless authenticated access and network egress controls are in place.
- Configure the narrowest possible `REDTEAM_ALLOWED_HOSTS`; do not use broad wildcard matching.
- Send only synthetic, non-sensitive probe content. The remote target receives every prompt and response in the conversation.
- The harness does not store assistant answer text, but the local report still reveals which probes were run and when.
- Protect and periodically delete reports. Do not commit them.
- Treat outcomes as incomplete heuristic evidence. A `resisted` result does not prove robustness.
- Review probe content and success regexes before execution. Malicious or excessive patterns can consume CPU.
- Pattern matching uses a time-limited regex engine; patterns that exceed the limit reject the probe outcome rather than blocking the service.
