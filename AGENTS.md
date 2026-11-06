# Blender Manual editing

## Before editing

- Read existing repository instructions and documentation style guidance.
- Inspect the target page and related documentation before making changes.
- Check Git status and preserve existing user edits.
- Verify behavior against the supplied Blender commit, source, or UI evidence.
- Identify uncertainty instead of inventing behavior.

## Writing

- Write reStructuredText with a maximum line length of 120 characters.
- Use straight quotes and avoid first- and second-person wording.
- Match Blender UI labels, capitalization, and grouping.
- Do not bold parameter names or add default values.
- Use enum field lists where appropriate.
- Distinguish operators from tools.
- Preserve reference targets, index entries, and cross-references.
- Keep changes focused; avoid unrelated rewrites.

## Validation

- Read the Makefile and build instructions before choosing a command.
- Build through the repository's make targets, not direct sphinx-build commands.
- Check changed references, image paths, indentation, and heading adornments.
- Report the build result and any unresolved warnings.
- Never claim visual verification without inspecting rendered output.

## Completion

- Summarize changed files and anything needing manual verification.
- Do not commit or push unless requested.
