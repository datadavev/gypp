gypp - readonly access to GPG YAML files
========================================

``gypp`` provides convenience methods for accessing entries in a GPG encrypted YAML file.

The YAML file has a structure like::

    # Comments start with a "#"
    DESCRIPTION: |
      This is a human readable description of this file.

    RECIPIENTS:
      - list of
      - recipients of
      - the encrypted file

    some_key:
      user: name of account (required)
      password: the password or phrase (required)
      name: human readable name of entry (optional)
      note: |
        optional note. The pipe char indicates that
        line breaks will be preserved, but the
        preceding space on each line will not.
      other: Other properties may be added as needed.

    another_key:
      user: some user
      password: password with a quote " in it
      name: another test entry
      note: |
        Same old stuff


Installation
------------

::

  pip install -U gypp


Use
---

List entries available::

  $ gypp my_passwords.gpg

  Source: junk.txt
  Description: This is a human readable description of this file.

  Keys available:
    some_key          : human readable name of entry (optional)
    another_key       : another test entry

Show a specific entry on the commandline::

  $ gypp -s -k some_key my_passwords.gpg

  user     : name of account (required)
  password :
  name     : human readable name of entry (optional)
  note
    optional note. The pipe char indicates that
    line breaks will be preserved, but the
    preceding space on each line will not.

  other    : Other properties may be added as needed.

Place password for entry on the clipboard::

  $ gypp -s -k some_key my_passwords.gpg
