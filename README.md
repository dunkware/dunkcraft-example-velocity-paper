# dunkcraft-example-velocity-paper

A production-ready example demonstrating the integration of Velocity proxy with Paper Minecraft server using Docker containers.

## Overview

This repository serves as a reference implementation for setting up a robust Minecraft server infrastructure using Velocity as a proxy server in conjunction with Paper Minecraft server. The setup addresses several common integration challenges and provides solutions for a reliable deployment. There are existing demos out there, that all did not work this one took me all night throught I would pust it for reference. The key things are getting environment variables to work in the docker-compose the correct configuration of many values for the proxy to talk to the back end server includes online-mode:false in server.properties, quite q few little things without great feedback on errors hope it helps someone. 

## Common Integration Challenges and Solutions

### 1. Environment Variable Management
**Challenge:** Environment variable conflicts between Docker Compose project naming and container configurations can lead to debugging difficulties.
- `COMPOSE_PROJECT_NAME` in bash profile conflicting with container names
- Velocity-specific environment variables requiring precise configuration

**Solution:**
- Explicit container naming in docker-compose.yml
- Clearly defined environment variable hierarchy
- Documentation of required environment variables

### 2. Configuration File Management
**Challenge:** Missing or incorrectly mounted configuration files can result in silent failures.
- paper-global.yml mounting issues
- Default configurations being used instead of custom ones
- GitHub-sourced config downloads overwriting local settings

**Solution:**
- Implemented `SKIP_DOWNLOADS: "true"` to prevent unwanted config overwrites
- Explicit volume mounting verification
- Comprehensive configuration file documentation

### 3. Network Configuration
**Challenge:** Port conflicts between Velocity proxy and Minecraft server components.
- RCON port (25575) conflicts between services
- Online-mode configuration mismatches

**Solution:**
- Disabled RCON for proxy service
- Standardized online-mode settings:
  - Velocity: `online-mode = false`
  - Paper: `online-mode = false`
- Proper port allocation and documentation

### 4. Security Considerations
- Forwarding secret implementation
- Proper authentication flow
- Network isolation between components

## Production Readiness Features

1. **Container Orchestration**
   - Docker Compose configuration
   - Kubernetes-compatible setup
   - Health check implementations

2. **Configuration Management**
   - Version-controlled configurations
   - Environment-specific overrides
   - Secure secret management

3. **Monitoring & Maintenance**
   - Container health checks
   - Log aggregation
   - Backup procedures

## Getting Started

Detailed setup instructions and configuration guidelines are provided in the repository documentation.

## License

This project is licensed under the MIT License - see the LICENSE file for details.
