# Google Calendar API Module Documentation

## `google_calendar` Class
Class for interacting with Google Calendar. This class provides methods to add, find, delete, and import events from Google Calendar, as well as parse `.ics` files for event details.

---

### `__init__(credentials_path='credentials.json', token_path='token.json')`
Initializes a `google_calendar` instance.

#### Arguments
- `credentials_path` (str): Path to the Google Calendar credentials file. Default is `'credentials.json'`.
- `token_path` (str): Path to the token file for authentication. Default is `'token.json'`.

#### Attributes
- `service` (`googleapiclient.discovery.Resource`): Google API service object for calendar interactions.
- `calendar_ids` (`pandas.Series`): Calendar IDs, with calendar names as indices.
- `primary_calendar` (str): Name of the primary calendar for the account.
- `primary_calendar_id` (str): ID of the primary calendar for the account.

---

### `add_event(start, end=None, duration=0, duration_units='H', title='Event', description=None, calendar_name=None, calendar_id=None, time_zone=None)`
Adds a single event to a Google Calendar.

#### Arguments
- `start` (str): Start time of the event. Format: `"January 4, 2022 4pm"`.
- `end` (str, optional): End time of the event. Default is `None`.
- `duration` (float, optional): Duration of the event. Default is `0`.
- `duration_units` (str, optional): Time units for duration. Default is `'H'` (hours).
- `title` (str): Title of the event. Default is `'Event'`.
- `description` (str, optional): Description of the event. Default is `None`.
- `calendar_name` (str, optional): Name of the calendar to add the event to. Default is `None`.
- `calendar_id` (str, optional): ID of the calendar to add the event to. Default is `None`.
- `time_zone` (str, optional): Time zone in TZ format. Default is `None`.

#### Raises
- `ValueError`: If `calendar_name` and `calendar_id` do not reference the same calendar.

---

### `find_future_events(title_contains=None, description_contains=None, calendar_name=None, calendar_id=None, maxResults=1000)`
Finds future events matching specified criteria.

#### Arguments
- `title_contains` (str, optional): Search keyword for the event title. Default is `None`.
- `description_contains` (str, optional): Search keyword for the event description. Default is `None`.
- `calendar_name` (str, optional): Name of the calendar to search. Default is `None`.
- `calendar_id` (str, optional): ID of the calendar to search. Default is `None`.
- `maxResults` (int): Maximum number of results to return. Default is `1000`.

#### Returns
- `list`: List of matching event dictionaries.

---

### `delete_events(events, calendar_name=None, calendar_id=None)`
Deletes events from a Google Calendar.

#### Arguments
- `events` (list): List of event dictionaries to delete.
- `calendar_name` (str, optional): Name of the calendar containing the events. Default is `None`.
- `calendar_id` (str, optional): ID of the calendar containing the events. Default is `None`.

#### Raises
- `ValueError`: If `calendar_name` and `calendar_id` do not reference the same calendar.

---

### `parse_ics(ics_path)`
Parses an `.ics` file into event data.

#### Arguments
- `ics_path` (str): Path to the `.ics` file.

#### Returns
- `list`: List of event dictionaries extracted from the `.ics` file.

---

### `make_multiple_events(title='Event', description=None, start_date, end_date=None, event_time=None, duration=None, duration_units='H', freq='B', periods=None, calendar_name=None, calendar_id=None, time_zone=None)`
Creates multiple recurring events in a Google Calendar.

#### Arguments
- `title` (str): Title of the events. Default is `'Event'`.
- `description` (str, optional): Description of the events. Default is `None`.
- `start_date` (str): Start date of the recurring events. Format: `"January 4, 2022"`.
- `end_date` (str, optional): End date of the recurring events. Default is `None`.
- `event_time` (str, optional): Time of the events. Default is `None`.
- `duration` (float, optional): Duration of each event. Default is `None`.
- `duration_units` (str): Units for the event duration. Default is `'H'` (hours).
- `freq` (str): Frequency of recurrence. Default is `'B'` (business days).
- `periods` (int, optional): Number of occurrences. Default is `None`.
- `calendar_name` (str, optional): Name of the calendar to add the events to. Default is `None`.
- `calendar_id` (str, optional): ID of the calendar to add the events to. Default is `None`.
- `time_zone` (str, optional): Time zone in TZ format. Default is `None`.

---

### `import_ics(ics_path=None, calendar_name=None, calendar_id=None, delete_ics=False)`
Imports events from an `.ics` file into a Google Calendar.

#### Arguments
- `ics_path` (str, optional): Path to the `.ics` file. Default is `None`.
- `calendar_name` (str, optional): Name of the calendar to import events into. Default is `None`.
- `calendar_id` (str, optional): ID of the calendar to import events into. Default is `None`.
- `delete_ics` (bool): Whether to delete the `.ics` file after import. Default is `False`.

#### Raises
- `ValueError`: If `calendar_name` and `calendar_id` do not reference the same calendar.
