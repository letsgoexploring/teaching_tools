# Gmail API Module Documentation

## authenticate_google_app
Authenticates and initializes a Google API service.

### Arguments
- `credentials_path` (str): Path to the credentials file for the Google API.
- `token_path` (str): Path to the token file for storing user authentication.
- `SCOPES` (list): List of scopes for the Google API service.
- `service_name` (str): Name of the Google API service (e.g., 'gmail', 'calendar').
- `service_version` (str): Version of the Google API service (e.g., 'v1', 'v3').

### Returns
- `googleapiclient.discovery.Resource`: Authenticated Google API service object.

---

## gmail Class
Class for managing and sending Gmail messages via the Google API.

### __init__
Initializes an instance of the `gmail` class.

#### Arguments
- `credentials_path` (str): Path to the Google API credentials file. Default: `'credentials.json'`.
- `token_path` (str): Path to the token file for authentication. Default: `'token.json'`.
- `sender` (str, optional): Default sender email address.

#### Attributes
- `service` (`googleapiclient.discovery.Resource`): Authenticated Gmail API service object.
- `sender` (str): Email address used as the default sender.

---

### add_message_label
Adds one or more labels to a Gmail message.

#### Arguments
- `message` (dict, optional): Message metadata dictionary. Default: `None`.
- `message_id` (str): ID of the message to label.
- `label_names` (str or list): Name(s) of the label(s) to add.
- `label_ids` (str or list): ID(s) of the label(s) to add.

#### Returns
- None

---

### delete_message
Permanently deletes a Gmail message.

#### Arguments
- `message` (dict, optional): Message metadata dictionary. Default: `None`.
- `message_id` (str): ID of the message to delete.

#### Returns
- None

---

### get_all_labels
Retrieves all Gmail labels for the user.

#### Returns
- `pandas.DataFrame`: DataFrame containing label names and metadata.

---

### get_from_sender
Finds all messages from a specific sender.

#### Arguments
- `sender` (str): Email address of the sender to search for.
- `label_name` (str, optional): Name of the Gmail label to filter messages by. Default: `None`.
- `label_id` (str, optional): ID of the Gmail label to filter messages by. Default: `None`.

#### Returns
- `list`: List of message metadata dictionaries. Returns `None` if no messages are found.

---

### get_label_id
Retrieves the ID of a Gmail label by its name.

#### Arguments
- `label_name` (str): Name of the label.

#### Returns
- `str`: Label ID.

---

### get_labeled_messages
Retrieves messages with a specific Gmail label.

#### Arguments
- `label_name` (str, optional): Name of the label. Default: `None`.
- `label_id` (str, optional): ID of the label. Default: `None`.

#### Returns
- `list`: List of message metadata dictionaries. Returns `None` if no messages are found.

---

### get_message
Retrieves a Gmail message by its ID.

#### Arguments
- `message` (dict, optional): Message metadata dictionary. Default: `None`.
- `message_id` (str, optional): ID of the message to retrieve. Default: `None`.

#### Returns
- `dict`: Full Gmail message data.

---

### get_message_return_path
Retrieves the 'Return-Path' header of a Gmail message.

#### Arguments
- `message` (dict, optional): Message metadata dictionary. Default: `None`.
- `message_id` (str, optional): ID of the message. Default: `None`.

#### Returns
- `str`: Email address from the 'Return-Path' header.

---

### get_return_paths
Retrieves 'Return-Path' headers from a list of messages.

#### Arguments
- `messages` (list): List of message metadata dictionaries.

#### Returns
- `list`: List of email addresses from the 'Return-Path' header.

---

### make_message
Creates and optionally sends a Gmail message.

#### Arguments
- `sender` (str, optional): Email address of the sender. Default: `None`.
- `to` (str or list, optional): Recipient email address(es). Default: `None`.
- `cc` (str or list, optional): CC email address(es). Default: `None`.
- `bcc` (str or list, optional): BCC email address(es). Default: `None`.
- `subject` (str): Email subject. Default: `'No subject'`.
- `plain_text` (str, optional): Plain text content of the email. Default: `None`.
- `html_text` (str, optional): HTML content of the email. Default: `None`.
- `markdown_text` (str, optional): Markdown content for the email. Default: `None`.
- `send` (bool): Whether to send the email immediately. Default: `True`.
- `attachments` (str or list, optional): Path(s) to attachment files. Default: `None`.

#### Returns
- `dict`: Sent message metadata if `send=True`, else draft metadata.

---

### move_message
Moves a Gmail message from one label to another.

#### Arguments
- `message` (dict, optional): Message metadata dictionary. Default: `None`.
- `message_id` (str, optional): ID of the message to move. Default: `None`.
- `old_label_name` (str): Name of the current label.
- `new_label_name` (str): Name of the target label.

#### Returns
- None

---

### move_messages
Moves a list of Gmail messages from one label to another.

#### Arguments
- `messages` (list, optional): List of Gmail messages. Each element is a dictionary with keys `'id'` and `'threadID'`. Default: `None`.
- `old_label_name` (str): Name of the current label to be removed.
- `new_label_name` (str): Name of the target label to be added.

#### Returns
- None

---

### remove_message_label
Removes one or more labels from a Gmail message.

#### Arguments
- `message` (dict, optional): Message metadata dictionary. Default: `None`.
- `message_id` (str): ID of the message to label.
- `label_names` (str or list): Name(s) of the label(s) to remove.
- `label_ids` (str or list): ID(s) of the label(s) to remove.

#### Returns
- None

---

### trash_message
Moves a Gmail message to the trash.

#### Arguments
- `message` (dict, optional): Message metadata dictionary. Default: `None`.
- `message_id` (str, optional): ID of the message to delete. Default: `None`.

#### Returns
- None
