# Escolar Management App (Flutter + Central Server)
Cross-platform mobile application built with Flutter (Dart) for managing an escolar transport and school service system. The application connects to a centralized backend server and supports multiple user roles (users, drivers, and service interactions).

The system provides real-time coordination between parents, drivers, and schools, including child assignment, contract management, notifications, and geolocation tracking.

---
## Overview

The application implements a client-server architecture:

```
Flutter Mobile App
        │
        ▼
REST API (Central Server)
        │
        ▼
Authentication + Database
        │
        ▼
Real-time updates (Socket.IO)
```

The app communicates exclusively with a backend API and uses persistent authentication via stored session tokens.

---

## Core Features
- Authentication & Accounts
- CPF-based login system
- User registration (standard user or driver)
- Persistent session storage (SharedPreferences)
- Role-based navigation (User / Driver)

---
## Driver Module

- Driver profile (name, vehicle plate, license info)
- Linked schools management
- View assigned children
- Add/remove school associations
- Contract management with parents

## User Module (Parents/Guardians)

- Profile with personal information
- Add/remove children
- Assign children to schools
- View assigned drivers per child
- Report child absence to driver

---

## Service Area
- Browse schools
- View available drivers per school
- Contract drivers for children
- Centralized school search with autocomplete

---
## Notifications System
- Contract requests (accept / reject)
- System notifications (acknowledge)
- Real-time updates via backend integration

---
## Map & Geolocation

- Driver location tracking
- Periodic GPS updates (drivers only)
- Live map-ready coordinate feed from backend
- Location sharing using device GPS (Geolocator)

---
## Real-Time Communication
- Socket.IO integration for live notifications
- Event-based updates from server
- Background connection management

## API Layer

Centralized API communication handled by ApiService.


### Main Endpoints
#### Authentication
- POST /register
- POST /login
#### User
- GET /profile
- GET /children
- POST /children
- DELETE /children
#### Driver
- GET /driver/profile
- GET /driver/children
- GET /driver/schools
#### Schools
- GET /schools
- POST /add_school
- POST /link_school
#### Contracts
- POST /contract_notification
- POST /accept_contract
- POST /reject_contract
#### Notifications
- GET /notifications
- POST /acknowledge_notification
#### Location
- GET /map
- POST /map

---

## State Management
- Local state handled via StatefulWidget
- Persistent session using SharedPreferences
- Role-based UI rendering (driver vs user)
- Manual refresh patterns after API calls

---
## Location System
- Uses geolocator for GPS tracking
- Drivers periodically send location updates
- Backend aggregates and serves driver positions
- Map page displays real-time coordinates list

---
## Notifications

Two types of notifications:

- Contract requests (accept/reject workflow)
- System alerts (acknowledge only)

Stored and fetched via API with manual refresh cycles.

---
## Dependencies
- Flutter
- Dart
- http
- shared_preferences
- socket_io_client
- geolocator
- flutter_typeahead

---
## Development Notes
- Designed for Android emulator and local backend testing
- Uses hardcoded base URL switching for emulator compatibility
- Minimal state management approach (no Provider/BLoC)
- API-driven UI updates (no local caching layer beyond session)

## Known Limitations
- No offline support
- No advanced state management architecture
- Location updates are periodic (not continuous streaming)
- UI is tightly coupled to API responses
- No formal error abstraction layer

## License

- Prototype / Academic project (non-commercial use unless otherwise specified)

## Video:

https://www.youtube.com/watch?v=60PWtvWq020
