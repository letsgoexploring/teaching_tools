# Gmail Class Documentation

The `gmail` class provides methods to interact with Gmail via the Google API, enabling functionalities such as sending emails, retrieving messages, managing labels, and creating drafts.

---

## Class: `gmail`

### Description
The `gmail` class allows email operations using Gmail’s API, such as sending messages, adding/removing labels, retrieving message metadata, and creating drafts.

---

### Initialization

#### Arguments:
- **`credentials_path`** *(str)*:  
  Path to the Google API credentials file. Default: `'credentials.json'`.
- **`token_path`** *(str)*:  
  Path to the token file for storing user authentication. Default: `'token.json'`.
- **`sender`** *(str, optional)*:  
  Default sender email address. Default: `None`.

#### Attributes:
- **`service`**:  
  Authenticated Gmail API service object.
- **`sender`** *(str)*:  
  Email address used as the default sender for outgoing emails.

---

## Methods

### `add_message_label`

**Description:**  
Adds labels to a Gmail message.

**Arguments:**
- **`message_id`** *(str)*:  
  ID of the message to label.
- **`label_names`** *(str or list)*:  
  Name(s) of the label(s) to add.

**Returns:**  
None

---

### `delete_message`

**Description:**  
Deletes a Gmail message.

**Arguments:**
- **`message_id`** *(str)*:  
  ID of the message to delete.

**Returns:**  
None

---

### `get_all_labels`

**Description:**  
Retrieves all Gmail labels for the user.

**Returns:**  
A pandas DataFrame containing label names and metadata.

---

### `get_from_sender`

**Description:**  
Finds all messages from a specific sender.

**Arguments:**
- **`sender`** *(str)*:  
  Email address of the sender to search for.
- **`label_name`** *(str, optional)*:  
  Name of the Gmail label to filter messages by. Default is None.
- **`label_id`** *(str, optional)*:  
  ID of the Gmail label to filter messages by. Default is None.

**Returns:**  
A list of message metadata dictionaries, or `None` if no messages are found.

---

### `get_label_id`

**Description:**  
Retrieves the ID of a Gmail label by its name.

**Arguments:**
- **`label_name`** *(str)*:  
  Name of the label.

**Returns:**  
The corresponding label ID as a string.

---

### `get_labeled_messages`

**Description:**  
Retrieves messages with a specific Gmail label.

**Arguments:**
- **`label_name`** *(str, optional)*:  
  Name of the label. Default is None.
- **`label_id`** *(str, optional)*:  
  ID of the label. Default is None.

**Returns:**  
A list of message metadata dictionaries, or `None` if no messages are found.

---

### `get_message`

**Description:**  
Retrieves a Gmail message by its ID.

**Arguments:**
- **`message_id`** *(str, optional)*:  
  ID of the message to retrieve. Default is None.
- **`message`** *(dict, optional)*:  
  Message metadata dictionary. Default is None.

**Returns:**  
The full Gmail message data as a dictionary.

---

### `make_message`

**Description:**  
Creates and optionally sends a Gmail message.

**Arguments:**
- **`sender`** *(str, optional)*:  
  Email address of the sender. Default is None.
- **`to`** *(str or list, optional)*:  
  Recipient email address(es). Default is None.
- **`cc`** *(str or list, optional)*:  
  CC email address(es). Default is None.
- **`bcc`** *(str or list, optional)*:  
  BCC email address(es). Default is None.
- **`subject`** *(str)*:  
  Email subject. Default is `'No subject'`.
- **`plain_text`** *(str, optional)*:  
  Plain text content of the email. Default is None.
- **`html_text`** *(str, optional)*:  
  HTML content of the email. Default is None.
- **`markdown_text`** *(str, optional)*:  
  Markdown content for the email. Default is None.
- **`send`** *(bool)*:  
  Whether to send the email immediately. Default is `True`.
- **`attachments`** *(str or list, optional)*:  
  Path(s) to attachment files. Default is None.

**Returns:**  
The metadata of the sent message if `send=True`, else the draft metadata.

---

### `trash_message`

**Description:**  
Moves a Gmail message to the trash.

**Arguments:**
- **`message_id`** *(str)*:  
  ID of the message to move to trash.

**Returns:**  
None

---

### `move_message`

**Description:**  
Moves a Gmail message from one label to another.

**Arguments:**
- **`message_id`** *(str, optional)*:  
  ID of the message to move. Default is None.
- **`message`** *(dict, optional)*:  
  Message metadata dictionary. Default is None.
- **`old_label_name`** *(str)*:  
  Name of the current label.
- **`new_label_name`** *(str)*:  
  Name of the target label.

**Returns:**  
None

---

### `move_messages`

**Description:**  
Moves multiple Gmail messages from one label to another.

**Arguments:**
- **`messages`** *(list, optional)*:  
  List of message metadata dictionaries. Default is None.
- **`old_label_name`** *(str)*:  
  Name of the current label.
- **`new_label_name`** *(str)*:  
  Name of the target label.

**Returns:**  
None
