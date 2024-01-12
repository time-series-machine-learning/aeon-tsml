# Releases

This page is to help core developers in releasing a new version of `aeon`.

Core developers making a release should have write access to the repository.

`aeon` aims for a release every one or two months currently, based on the amount of
new content available for the release.

## Preparing the release version

The release process is as follows, on high-level:

1. __Ensure deprecation actions are carried out.__
  Deprecation actions for a version should be marked by "version number" annotated
  comments in the code. E.g., for the release 0.10.0, search for the string 0.10.0 in
  the code and carry out described deprecation actions. Collect list of deprecation
  actions, as they should go in the release notes.

2. __Create a "release" pull request.__
  Create a branch from main and PR named after the release version. This should make
  changes to the version numbers (root `__init__.py`, `README.md` and `pyproject.toml`)
  and have complete release notes in the changelog webpage.

3. __Merge the "release" pull request.__
  This PR should ideally be the final PR made before the release with the exception of
  any necessary troubleshooting PRs. The PR and release notes should optimally be
  reviewed by the core developers, then merged once tests pass.

4. __Create the GitHub release by following the steps below.__
  This release should create a new tag and a release on GitHub following the steps below:
1. Go to the repository's Releases tab on GitHub and click on 'Draft a new release'.
2. Enter the tag following the syntax v[MAJOR].[MINOR].[PATCH], e.g., v0.10.0 for version 0.10.0.
3. Set the release name as `aeon v0.10.0`.
4. In the GitHub release notes, include the following sections:
   - Highlights
   - New contributors
   - All contributors
5. Link to the release notes in the changelog using a reference link.
6. Include the full GitHub commit log between releases in the release notes.

## ``pypi`` release and release validation

Ensure that the release workflow is triggered and completes successfully.

5. __Wait for the ``pypi`` release CI/CD to finish.__
  If tests fail due to sporadic unrelated failure, restart. If tests fail genuinely,
  something went wrong in the above steps, investigate, fix, and repeat.

6. __Release workflow completion tasks.__
  Check the version of `aeon` on PyPI to verify that the new version has been released. A validatory installation of `aeon` in a new Python environment
  should be carried out according to the installation instructions. If the installation
  does not succeed or wheels have not been uploaded, action to diagnose and remedy must
  be taken.

## Release notes

Release notes can be generated using the `build_tools/changelog.py` script, and should
be placed at the top of the relevant [MINOR] versions webpage. e.g.,
`docs/chanelogs/v0.10.md` for version 0.10.0. Generally, release notes should follow the
general pattern of previous release notes, with sections:

- Highlights
- Dependency changes, if any
- Deprecations/removals, if any.
- - - - Auto generated PR and contributions sections.

  [Link to the commit log](commit_log_link)

  [Link to the commit log](commit_log_link)

  [Link to the commit log](commit_log_link)
