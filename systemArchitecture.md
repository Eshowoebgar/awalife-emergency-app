# System Architecture: AwaLife

## An Overview
AwaLife is a cross-platform mobile app that connects users to verified paramedic companies and nearby hospitals.

## AwaLife Stack
- **Frontend**: React Native (or Flutter) - builds Android and iOS apps from one codebase.
- **Backend**: PHP (Laravel) - handles requests, authentication, and partner messaging.
- **Database**: MySQL - stores users, paramedic partners, hospital data, requests, and logs.
- **Messaging**: Push notifications (Firebase Cloud Messaging) and SMS fallback.
- **Maps**: Google Maps or OpenStreetMap for hospital & ambulance locations.

## How AwaLife works
1. **Mobile App (User)**  
   - User presses HELP → app sends `POST /requests` to backend with location and emergency type.
2. **Backend (Laravel API)**  
   - Validates request → finds nearest paramedic partner → sends push notification/SMS to partner.
   - Stores the request in MySQL and updates status (pending → accepted → enroute → completed).
3. **Paramedic Partner App / Dashboard**  
   - Partner receives request → accepts → updates status → backend notifies user with ETA.
4. **Hospital Directory**  
   - Backend returns hospitals with required facilities (ICU, trauma, blood availability) for the emergency type.
5. **Telemetry & Logs**  
   - All requests logged for audits, performance and future analytics.


## Data flow (simple diagram)
User App --- Backend API --- Database
Backend --- Push/SMS --- Paramedic Partner
Backend --- Map Service --- User App (to show hospitals and ambulance ETA)



## Why AwaLife is Technically Feasible 
- **React Native** or **Flutter** let's us build one app for both phones fast.
- **Laravel and MySQL** are proven and simple for quick backend builds.
- Push notifications and SMS ensure partners get alerts even when internet is flaky.
- Map APIs are already available and reliable for location services.


  
## AwaLife Security & Privacy (short)
- Authenticate users and partners with tokens.  
- Store only needed patient/location info and encrypt sensitive fields.  
- Keep logs for 30–90 days and follow local privacy rules.



## Next steps for developers
1. Build API endpoints (`/requests`, `/partners`, `/hospitals`).  
2. Create partner dashboard (web or small app).  
3. Hook up push notifications and SMS gateway.  
4. Seed database with partner & hospital test data.



## #Diagram coming soon!
