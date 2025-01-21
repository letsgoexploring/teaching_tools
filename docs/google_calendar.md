# Google Calendar Class Documentation

The `google_calendar` class provides methods for interacting with Google Calendar, including functionalities to add, find, delete, and import events, as well as parse `.ics` files.

---

## Class: `google_calendar`

### Description
The `google_calendar` class allows interaction with Google Calendar via the Google API, enabling users to manage events and calendars programmatically.

---

### Initialization

#### Arguments:
- **`credentials_path`** *(str)*:  
  Path to the Google Calendar credentials file. Default: `'credentials.json'`.
- **`token_path`** *(str)*:  
  Path to the token file for storing user authentication. Default: `'token.json'`.

#### Attributes:
- **`service`**:  
  Authenticated Google API service object for calendar interactions.
- **`calendar_ids`** *(pandas.Series)*:  
  Calendar IDs, with calendar names as indices.
- **`primary_calendar`** *(str)*:  
  Name of the primary calendar for the account.
- **`primary_calendar_id`** *(str)*:  
  ID of the primary calendar for the account.

---

## Methods

### `add_event`

**Description:**  
Adds a single event to a Google Calendar.

**Arguments:**
- **`start`** *(str)*:  
  Start time of the event. Format: `"January 4, 2022 4pm"`.
- **`end`** *(str, optional)*:  
  End time of the event. Default is `None`.
- **`duration`** *(float, optional)*:  
  Duration of the event in specified units. Default is `0`.
- **`duration_units`** *(str, optional)*:  
  Time units for the duration. Default is `'H'` (hours).
- **`title`** *(str)*:  
  Title of the event. Default is `'Event'`.
- **`description`** *(str, optional)*:  
  Description of the event. Default is `None`.
- **`calendar_name`** *(str, optional)*:  
  Name of the calendar to add the event to. Default is `None`.
- **`calendar_id`** *(str, optional)*:  
  ID of the calendar to add the event to. Default is `None`.
- **`time_zone`** *(str, optional)*:  
  Time zone for the event in TZ format. Default is `None`.

**Raises:**  
`ValueError` if `calendar_name` and `calendar_id` do not reference the same calendar.

**Returns:**  
None

---

### `find_future_events`

**Description:**  
Finds future events matching specified criteria.

**Arguments:**
- **`title_contains`** *(str, optional)*:  
  Search keyword for the event title. Default is `None`.
- **`description_contains`** *(str, optional)*:  
  Search keyword for the event description. Default is `None`.
- **`calendar_name`** *(str, optional)*:  
  Name of the calendar to search. Default is `None`.
- **`calendar_id`** *(str, optional)*:  
  ID of the calendar to search. Default is `None`.
- **`maxResults`** *(int)*:  
  Maximum number of results to return. Default is `1000`.

**Returns:**  
A list of matching event dictionaries.

---

### `delete_events`

**Description:**  
Deletes events from a Google Calendar.

**Arguments:**
- **`events`** *(list)*:  
  List of event dictionaries to delete.
- **`calendar_name`** *(str, optional)*:  
  Name of the calendar containing the events. Default is `None`.
- **`calendar_id`** *(str, optional)*:  
  ID of the calendar containing the events. Default is `None`.

**Raises:**  
`ValueError` if `calendar_name` and `calendar_id` do not reference the same calendar.

**Returns:**  
None

---

### `parse_ics`

**Description:**  
Parses an `.ics` file into event data.

**Arguments:**
- **`ics_path`** *(str)*:  
  Path to the `.ics` file.

**Returns:**  
A list of event dictionaries extracted from the `.ics` file.

---

### `make_multiple_events`

**Description:**  
Creates multiple recurring events in a Google Calendar.

**Arguments:**
- **`title`** *(str)*:  
  Title of the events. Default is `'Event'`.
- **`description`** *(str, optional)*:  
  Description of the events. Default is `None`.
- **`start_date`** *(str)*:  
  Start date of the recurring events.
- **`end_date`** *(str, optional)*:  
  End date of the recurring events. Default is `None`.
- **`event_time`** *(str, optional)*:  
  Time of the events. Default is `None`.
- **`duration`** *(float, optional)*:  
  Duration of each event. Default is `None`.
- **`duration_units`** *(str)*:  
  Units for the event duration. Default is `'H'` (hours).
- **`freq`** *(str)*:  
  Frequency of recurrence. Default is `'B'` (business day).
- **`periods`** *(int, optional)*:  
  Number of occurrences at the specified frequency. Default is `None`.
- **`calendar_name`** *(str, optional)*:  
  Name of the calendar to add the events to. Default is `None`.
- **`calendar_id`** *(str, optional)*:  
  ID of the calendar to add the events to. Default is `None`.
- **`time_zone`** *(str, optional)*:  
  Time zone for the events. Default is `None`.

**Returns:**  
None

---

### `import_ics`

**Description:**  
Imports events from an `.ics` file into a Google Calendar.

**Arguments:**
- **`ics_path`** *(str, optional)*:  
  Path to the `.ics` file. Default is `None`.
- **`calendar_name`** *(str, optional)*:  
  Name of the calendar to import events into. Default is `None`.
- **`calendar_id`** *(str, optional)*:  
  ID of the calendar to import events into. Default is `None`.
- **`delete_ics`** *(bool)*:  
  Whether to delete the `.ics` file after import. Default is `False`.

**Raises:**  
`ValueError` if `calendar_name` and `calendar_id` do not reference the same calendar.

**Returns:**  
None
