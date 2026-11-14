# Contributing

Thanks for helping make Motion Graphics Skills better.

## Ways to help
- **Report a bug:** open an issue with the skill name, what you asked, and what went wrong (a screenshot or short clip helps).
- **Request a style:** open a "Style request" issue with a reference video or a description of the look.
- **Fix a skill:** edit `skills/<folder>/SKILL.md` (and the matching `google_flow_prompts/<folder>/prompt.md`) and open a pull request.

## Pull requests
1. Fork the repo and create a branch.
2. Keep one skill (or one fix) per pull request.
3. Test the skill in Claude Code on a short clip before submitting.
4. Run `claude plugin validate . --strict` if you changed anything in `.claude-plugin/`.
5. Describe what changed and attach a before/after frame if it is visual.

## Rules for new skills
- Original names, demo text and colours; do not copy a creator's or brand's look one to one.
- Never alter the user's footage; only add captions, graphics and layouts around it.

By contributing you agree your work is released under the [MIT License](LICENSE).
