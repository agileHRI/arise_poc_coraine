# Contributing to arise_poc_coraine

Thanks for looking at the ARISE PoC with coraine. These guidelines say where help is useful and under
what terms contributions are accepted. They follow [coraine's](https://github.com/SEAMWARE/coraine/blob/main/CONTRIBUTING.md).

## Ground rules

- Be kind and thoughtful. This project is released with a [Contributor Code of Conduct](./CODE_OF_CONDUCT.md).
  By participating, you agree to abide by its terms.
- If you open a pull request, you must sign the
  [Individual Contributor License Agreement](https://fiware.github.io/contribution-requirements/individual-cla.pdf)
  by stating in a comment: *"I have read the CLA Document and I hereby sign the CLA"*.
- Contributions are accepted under the [Apache License 2.0](./LICENSE), the licence this project is
  distributed under. Every file that can hold a comment carries an SPDX identifier; keep it.
- Do not copy files from the original ARISE PoC (`Engineering-Research-and-Development/arise-poc`):
  it is licensed under AGPL-3.0, which is not compatible with this repository's licence.

## How to contribute

- **Minor contribution** (a fix, a dashboard tweak): open a pull request.
- **Major contribution** (a new part of the PoC, such as OPC UA): open an issue first.

Pull requests go against `main`, one subject each. A change must be **tested end to end**
(`docker compose up`, turtles moving, data in coraine, the dashboards and c³), and the pull request says
what was checked. A change a user would notice gets a [CHANGELOG](CHANGELOG.md) entry.

Every change is reviewed by a maintainer (see [`.github/CODEOWNERS`](.github/CODEOWNERS)).

## Maintainers

- Ken Zangelin ([@kzangeli](https://github.com/kzangeli))
- Francisco Meléndez ([@FcoMelendez](https://github.com/FcoMelendez))
