=========================================================
# Status Dashboard 3 (SD3) High Level Architecture Design
=========================================================

**Status Dashboard 3 (SD3)** is a component within the **Stackmon** ecosystem. It serves two primary purposes:
1. Displaying status information in a dashboard using green, yellow, or red semaphore lights.
2. Maintaining and managing event states for Service Managers who review, describe, or manage such events.
   
The actual measurement of the metrics, its preprocessing, storage in a time series database, aggregation and
mapping to specific incident states is out of scope of this component. These tasks are covered by the
Stackmon backend components.

## Context and Scope

- **Context**: SD3 is part of the Stackmon system (URL).
- **Scope**:
  - SD3 separates scheduling, actual measurement, aggregation, and severity assessment from the display
    function. Only the latter is in scope of the component.
  - It should be developed as a web application.
  - The application should use React as the front-end framework.
  - It should integrate with the One Experience framework.

## Interfaces

### Incoming Data
1. **Incident Data**: SD3 receives incident data from the metric processor (not in scope for this document).

### User Interaction
2. **User Data**: SD3 displays and manages user data to visualize the state with semaphores as a website,
   utilizing React and OneExperience.
3. **Service Interface**: SD3 provides updated status information for third-party components such as mobile
   applications (via an RSS feed) or enterprise monitoring systems.
4. **Incident Management**: Users, such as Managers on duty or Service Managers, can manage incident situations.

### Data Storage
4. **Incident data** and their annotations are stored in an external persistent database.
   
### Interface Types
- REST
- Web
- RSS
- Websockets
- ODBC

## Components

### Application Core
The core application consists of three APIs:
1. **Database API**: Connects to the data storage system.
2. **User API**: Interfaces with web applications (HTML, mobile apps, etc.).
3. **Service Manager API**: Interfaces with service management tools (web, HTML).

## Data Storage

- **Type of Database**: To be determined.
- **Connector**: Interface for connecting the database to the application.

## Authentication and Security

The application processes no personal data and is in its main functions displaying just
public data. Some functions like manipulations or annotations to actual incident data
(including the reason why and when an incident ended) need authorization. For this feature
users have to authenticate themselves and are required to be a member of a group. This
auth data is provided by an external auth plaugin (Keycloak).


## Glossary and Definitions

- **Frontend**: The client-side of the application where users interact.
- **Backend**: The server-side of the application that processes data and handles business logic.
- **Stackmon**: The ecosystem that SD3 is a part of.
- **Semaphore**: Visual indicators (green, yellow, red) representing status.
- **Incident**: An event that needs to be managed by the system.
- **User**: ...
- **Service Manager**: ...

## Architecture Decision Records

- **Decision 1**: Use React as the front-end framework.
- **Decision 2**: Integrate with the One Experience framework.
- **Decision 3**: Use REST, Web, RSS, Websockets, and ODBC for interfaces.

This Markdown format can be easily used for documentation purposes, providing clear sections for each aspect of the architecture design for "Status Dashboard 3".
