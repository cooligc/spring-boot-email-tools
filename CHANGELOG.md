# Change Log
All notable changes to Spring-Boot-Email-Tools project will be documented in this file.
This project adheres to [Semantic Versioning](http://semver.org/).


## [Planned]
- Revise unit testing by only using AssertJ and JUnit5.
- Append a listener to be notified on email sent.

## [Unreleased]


## [0.5.0] - 2017-02-26
### Added 
- Annotation to avoid using `@ComponentScan` in the spring boot main application (refer to issue #32).
### Changed
- Large refactoring of packages.
### Fixed
- Class `PriorityQueueSchedulerService` has been simplified, with a large refactoring to provide
    better interaction with persistence service (now having it own thread).

## [0.4.2] - 2017-02-21
### Added
- More examples with scheduling and persistence.
- New config key for REDIS settings `spring.mail.scheduler.persistence.redis.settings`.

### Fixed
- Fixed concurrency issues in the scheduler.
- Used new version of EmbeddedRedis that shutdown the `ThreadExecutor` properly.

## [0.4.1] - 2017-02-14
### Added
- The property to enable the `SchedulerService` class is the boolean one `spring.mail.scheduler.enabled`.
- The application property `spring.mail.scheduler.enabled.priorityLevels` for the default scheduler 
    class `PriorityQueueSchedulerService` is required on if `spring.mail.scheduler.enabled=true`.
- The main properties in `application.properties` required by the extension are now hardcoded 
    in class `ApplicationPropertiesConstants`.

### Changed
- The `SchedulerService` is not enabled by default anymore, it needs to be activated via `application.properties`.
- The `PersistenceService` is becomes enabled if the proper properties are provided plus if the `SchedulerService` 
    is enabled as well.
- The application properties `spring.mail.persistence.*` are now renamed into `spring.mail.scheduler.persistence.*`, 
    since they can work only with the scheduler.
- The application properties `spring.mail.scheduler.persistenceLayer.*` are now renamed into `spring.mail.scheduler.persistence.*`.

## [0.4.0] - 2017-02-08
### Added
- Persistence has been introduced with optional `PersistenceService`: default implementation relies on embedded-REDIS. 
- GreenMail is used for integration tests with `EmailService` in order to increase the coverage after recent bugs.

### Changed
- All the classes ending with `Impl` are now renamed by removing the suffic and by starting with `Default`. Moreover, 
 the package containing these classes has been renamed from `impl` to `defaultimpl`.
- Using Spring Boot _1.5.1.RELEASE_
- Using Pebble _2.3.0.RELEASE_
- The default scheduler class `PriorityQueueSchedulerService` requires the property `spring.mail.scheduler.enabled.priorityLevels`.

## [0.3.8] - 2017-02-03
### Fixed
- Fixed NPE when attachments were missing (issue 19)

## [0.3.7] - 2017-01-09
### Fixed
- Support to email attachment has been fixed by removing the content type of attachments (issue 15)

## [0.3.6] - 2017-01-05
### Changed
- Using Spring Boot _1.4.3.RELEASE_
### Fixed
- Support to email attachment has been fixed (issue 15)

## [0.3.5] - 2017-01-04
### Added
- Added receipt notification in email header

## [0.3.4] - 2016-07-05
### Changed
- Using Spring Boot _1.3.6.RELEASE_

## [0.3.3] - 2016-07-01
### Fixed
- Corrected annotation for autowiring beans in `README.md`
- Made `TemplateService` optional in `EmailService`

## [0.3.2] - 2016-05-26
### Added
- Added support for **Thymeleaf** (version from Spring Boot _1.3.5.RELEASE_)

## [0.3.1] - 2016-05-14
### Changed
- Using Spring Boot _1.3.5.RELEASE_

## [0.3.0] - 2016-05-14
### Added
- Added support for **Mustache** (version from Spring Boot _1.3.4.RELEASE_)
  and **Pebble** (_version 2.2.1_)

### Changed
- Main module changed to `spring-boot-email-core` to support generic template engines
- Added specific modules based on known template engines (Freemarker, Mustache and Pebble)

### Fixed
- Closing mechanism of the scheduler is now responsive

## [0.2.0] - 2016-05-12
### Added
- Added implementation of a scheduler service with class `PriorityQueueSchedulerService`

### Changed
- Using Spring Boot _1.3.4.RELEASE_
- Increased dependencies version
- Removed dependency `zalando/problem-spring-web` (you can handle exceptions as you prefer)

## [0.1.1] - 2016-03-09
### Fixed
- Minor bugfix for detecting mime type when not set for an email.

### Changed
- Increased dependencies version

### Added
- Added more unit test to increase coverage

## [0.1.0] - 2016-01-26
### Added
- Basic implementation with an `EmailService` that may use the Freemarker template engine .
