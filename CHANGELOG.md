# Changelog
All notable changes to this project will be documented in this file.

## [Unreleased]

## [1.9.0] - 2018-02-15
### hubzone-sprint-36
### Changed
  - HUB-1133
    - Changes the Likely QDA logic to not show Likely QDAs for QCT_E and QNMC_E due to the updating rules imposed by NDAA 2018.

## [1.8.5] - 2018-01-05
### hubzone-sprint-33
### Added
  - HUB-1033 Adds in a Poirot pre-commit template and a rake task for adding this to the local users `.git/hooks` folder.
### Changed
  - HUB-1033 Tweaks the Poirot patterns a bit.

## [1.8.4] - 2017-12-22
### hubzone-sprint-32

Prepared repository for open source release.

### Added
  - LICENSE
  - CONTRIBUTING.md
  - code.json

## [1.8.3] - 2017-12-08
### hubzone-sprint-31
### Changed
  - HUB-984 Remove Google API keys from the config files -- use .env file instead

## [1.8.2] - 2017-11-22
### hubzone-sprint-30
### Changed
  - HUB-986
    - Guards against an invalid statement in an assertion query.  This will protect the system if the geo database has not been updated with new tables that the api is expecting.

## [1.8.1] - 2017-11-10
### hubzone-sprint-29
### Changed
  - HUB-934
    - Changes the business logic for when the `likely_qda_designations` array is returned depending on the other present hubzone statuses.  Refer to confluence for details about details of this [likely_qda display decision tree](https://sbaone.atlassian.net/wiki/spaces/FEAR/pages/93880465/Likely+QDA+Display+Decision+Tree)
    - Includes the entire qda designation data structure in the `likely_qda` information to help in diffing between the likely_qda and a `qct_qda` or `qnmc_qda`.

## [1.8.0] - 2017-10-27
### hubzone-sprint-28
### Added
  - HUB-889
    - Adds in the call to the congressional districts layer.
    - Wraps calls to non-HUBZone layers for a location in a new abstracted method `append_other_information()`, which includes congressional districts and likely_qda

## [1.7.0] - 2017-10-12
### hubzone-sprint-27
### Added
  - HUB-877
    - This ticket adds in the concept of `likely_qda` designations for a location. In HUBZone ETL, a new public view was created that contains declarations and county geometries for all disasters defined in the most recent disaster import table.
    - After checking for HUBZone designations, the API will also check the `likely_qda` table and append these to the response under the following update to the response structure:
    ```
      {
        ...,
        hubzone: [same as before, HUBZone designations go here],
        other_information: {
          alerts: {
            likely_qda_designations: [
              {
                "incident_description": <text description of the disaster>,
                "qda_declaration": <date of disaster declaration>
              }
            ]
          }
        },
        ...
      }
    ```
    - The `likely_qda` designation does not interact with the HUBZone designations at all, either in when designations are checked, or in the response structure.

## [1.6.0] - 2017-10-13
### hubzone-sprint-27
### Added
  - This Changelog
### Fixed

  - HUB-885
    - Fixed failing tests for version controller

  - HUB 859
    - Updated gems and addressed rubocop concerns
