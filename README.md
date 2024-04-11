# Unified Device Management System

This repository is a monorepo for the Unified Device Management System, which integrates various components necessary for managing SCCM devices via a Ruby script, a Rails-based web interface, and an iOS application. Each subproject is designed to operate both independently and together, offering a flexible approach to device management.

## Components

The system is divided into the following components:

1. **Ruby Script Loader**
   - **Purpose**: Automates the process of loading JSON data about SCCM devices into a Redis database.
   - **Technology**: Ruby

2. **Rails Web Application**
   - **Purpose**: Provides a web interface for searching devices within the Redis database and offers an API for external systems to access the device data.
   - **Technology**: Ruby on Rails

3. **iOS Application**
   - **Purpose**: Enables mobile access to the device data, allowing searches and management operations from iOS devices like iPhones and iPads.
   - **Technology**: Swift

## Repository Structure

```
/project-root
    /json-to-redis         # Ruby script for loading JSON into Redis
    /web-app            # Rails application for device search
    /ios-app               # Swift project for iOS app
    /common                # Any common code or resources
    /docs                  # Documentation for the whole project
    /.github/workflows     # CI/CD scripts using GitHub Actions
```

## Getting Started

### Prerequisites

- Redis server (for deployment)
- Ruby 3.0 or later
- Rails 7.1.2 or later
- Xcode 12 or later (for iOS app development)

### Local Setup

1. **Ruby Script:**
   ```bash
   cd json-to-ruby
   bundle install
   ruby load_json_to_redis.rb
   ```

2. **Rails Site:**
   ```bash
   cd web-app
   bundle install
   rails db:migrate
   rails db:seed
   rails server
   ```

3. **iOS App:**
   ```bash
   cd ios-app
   pod install
   open DeviceManager.xcworkspace
   ```

### Environment Variables

- `REDIS_URL`: URL for the Redis server, used by both the Ruby script and Rails site.
- `REDIS_PASSWORD`: Password for the REDIS database.

## Continuous Integration and Deployment

GitHub Actions are configured to handle CI/CD for each component independently based on changes to their respective directories:

- **Ruby Script**: Automated tests and deployment trigger on updates to `/json-to-redis/**`.
- **Rails Site**: Automated tests, security checks, and deployment trigger on updates to `/web-app/**`.
- **iOS App**: Automated build and test execution trigger on updates to `/ios-app/**`.

## License

[MIT License](LICENSE.md)

---

### Notes on Customization

You may need to adapt paths, specific commands, and other configurations to match the actual setup of your development environment and deployment routines. Make sure that the README is kept up-to-date as the project evolves.

This template provides a clear, straightforward introduction to your project for any new developers joining the project or external contributors. It’s also structured to facilitate easy navigation and understanding of the project's components and their relationships.
