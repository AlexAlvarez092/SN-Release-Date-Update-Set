# Set Release Date in the Update Set

[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![license-shield]][license-url]

Populate the *release date* attribute as soon as the update set is committed in the higher environment.

## Installation

- Option 1. Cloning repository
- Option 2. Committing [update set](./releases/release_date_v100.xml)

## Dependencies

- **Update source** configured
- Update set **retrieved from remote update source**

## Technical solution

### Destiny

Stuff installed in the environment where the update set is committed.

#### Business rule

- `Post release date to lower environment`: Triggered after committing a new update set from an update source. Inserts a new event `release_date.send_to_lower_env` in the queue.

#### Events

- Event registered: `release_date.send_to_lower_env`
- Script action: Post a REST message to the update source

#### System properties

| Property name | Description |
| ------------- | ----------- |
| `release_date.resource_path` | Stores the endpoint of the API in the source environment |

### Source

#### REST API

- Resource: [POST] Release date
  - Query parameter(s)
    - Update set sys_id
    - Commitment date


[contributors-shield]: https://img.shields.io/github/contributors/AlexAlvarez092/SN-Release-Date-Update-Set.svg?style=for-the-badge
[contributors-url]: https://github.com/AlexAlvarez092/SN-Release-Date-Update-Set/graphs/contributors

[forks-shield]: https://img.shields.io/github/forks/AlexAlvarez092/SN-Release-Date-Update-Set.svg?style=for-the-badge
[forks-url]: https://github.com/AlexAlvarez092/SN-Release-Date-Update-Set/network/members

[stars-shield]: https://img.shields.io/github/stars/AlexAlvarez092/SN-Release-Date-Update-Set.svg?style=for-the-badge
[stars-url]: https://github.com/gAlexAlvarez092/SN-Release-Date-Update-Set/stargazers

[issues-shield]: https://img.shields.io/github/issues/AlexAlvarez092/SN-Release-Date-Update-Set.svg?style=for-the-badge
[issues-url]: https://github.com/AlexAlvarez092/SN-Release-Date-Update-Set/issues

[license-shield]: https://img.shields.io/github/license/AlexAlvarez092/SN-Release-Date-Update-Set.svg?style=for-the-badge
[license-url]: https://github.com/AlexAlvarez092/SN-Release-Date-Update-Set/blob/master/LICENSE.txt
