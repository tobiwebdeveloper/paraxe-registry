# Booking01

A scheduling layout for consultations, tutoring, introductions, and service appointments. Its editorial introduction leads into a three-part frame: service/host brief, inline month calendar, and available local times. Choosing a time replaces the date grid with a guest-details form and a persistent appointment summary. Confirmation has its own composition with a reference and calendar download. Studio is the suggested recipe; the block continues to consume the active palette, typography, density, radius, surfaces, and component variants.

The service brief moves above the working area on smaller screens. At mobile widths the calendar and times stack, time buttons form wrapping pairs, and details become a single column. Text can wrap inside each region. Brand, host, agenda, copy, imagery, dates, time zones, and destinations are editable source/data.

Try `?preview=booking-01&profile=studio&theme=light` in either playground. Booking01 appears under **In progress**, outside immutable registry 0.2.0. It requires the new core Calendar and matching development framework/design packages. The current npm archives and installable registry bundles are unchanged.

## Use the block

Copy the Vue default or named React Booking01 entry with shared booking.ts and booking.css. Keep a stable controller per mounted booking/session; server applications must create a separate controller for each request/user.

```ts
import {
  createBookingController, BookingSlotUnavailableError,
} from './blocks/booking-01/shared/booking';

const controller = createBookingController(serviceRecord, {
  async confirm(request) {
    const result = await appointmentService.reserve(request);
    if (result.status === 'unavailable') throw new BookingSlotUnavailableError();
    return result.confirmation;
  },
});
```

appointmentService is your application adapter. Vue passes `:controller="controller"`; React passes `controller={controller}`. Optional title, description, backHref, and refresh customize the page. backHref and an optional confirmed joinHref accept relative or HTTPS destinations. refresh is an application action, shown for empty availability; use it to fetch and replace the schedule.

## Service and time data

BookingRecord contains id, brand, title, description, host, durationMinutes, location, language, agenda, asOf, locale, timeZone, timeZones, and slots. Host has name, role, and optional imageSrc; initials are the default fallback. Slot records have unique id, unique start instant, and an explicit available boolean. IDs use letters/numbers with optional hyphens/underscores. Duration is a positive integer of at most 1,440 minutes. Record and nested arrays/objects are copied and frozen.

asOf and each slot start are timestamp strings with an explicit timezone. asOf records when the supplied availability snapshot was current. Slots at/before asOf are excluded; confirm also checks the current clock. The UI does not poll or expire entries on a timer. A production adapter must refresh availability and independently enforce current time, host availability, duration, permissions, overlap prevention, and request idempotency on the server.

timeZones is a nonempty list of unique IANA values and visible labels; the default timeZone must be offered. Dates are grouped by the selected zone. Changing zone retains the selected instant and updates its displayed date. Time buttons show UTC offsets so repeated daylight-saving clock times remain distinguishable. Locale formats dates/times; the current interface copy is English and editable in the copied entries.

## State, confirmation, and recovery

The controller offers getSnapshot, subscribe, availability, setDate, setTimeZone, choose, edit, back, confirm, replace, reset, and cancelPending. Snapshots are immutable. The phases are choose, details, and confirmed. Name/email are required; the optional notes field is limited to 2,000 characters. Application validation and persistence remain authoritative.

confirm receives copied requestId, serviceId, slot, details, and timeZone. The default request ID uses Web Crypto randomUUID; services can inject createRequestId and now for their environment/tests. A generic retry with unchanged details/slot/zone keeps its request ID. Editing or changing the request creates a fresh key. Pending work guards duplicate submissions and edits.

A service must return id, matching slotId, matching start instant, createdAt, and optional joinHref. The controller validates the response before showing confirmation. A failure keeps the details and permits retry. BookingSlotUnavailableError excludes that slot locally and returns to available choices while preserving the draft. A successful reset excludes the booked slot locally before starting again; it does not cancel the appointment. replace(record) resets local selection/draft and invalidates an outstanding response. cancelPending invalidates a local response but does not abort the request or undo a server reservation. The app owns navigation cleanup and reconciliation with external work.

## Calendar artifact and preview boundary

The confirmed download creates an actual `.ics` event with UTC start/end, confirmation reference, and public service description/location. It uses CRLF lines, escaped text, and UTF-8 line folding following [RFC 5545](https://www.rfc-editor.org/rfc/rfc5545). Guest notes/email are excluded. The file can be imported by the visitor; downloading does not send invitations, create a video meeting, email participants, or write to a calendar account. Hosts requiring provider sync must implement it in their application service. Strict Content Security Policies may require replacing the data URL with an app-owned download endpoint.

The preview has fictional host/availability data and a local confirmation adapter, with controls for service failure, slot conflict, and empty availability. No external reservation or email is created. The new [Calendar](../components/calendar.md) stays focused on date selection; booking rules live in the copied controller/application.

Checks cover date arithmetic, month/year keyboard movement, availability, time-zone grouping and repeated DST times, duplicate/stale requests, retries, conflicts, linked forms, confirmation, and event serialization. Both framework renders and Vue client transitions are exercised. Token checks, typechecks, and production builds complement those tests. Browser visual/native review remains pending when no connection is available.
