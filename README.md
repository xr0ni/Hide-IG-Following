# Hide IG Following

*** PATCHED AS OF 22 NOV 2026, CODE LEFT UP FOR REVIEW ***

Toggle hidden Instagram privacy settings that aren't exposed in the app.

**What it does:**

- **Hide followers/following list** — your follower and following lists become "hidden due to privacy" to other users.
- **Hide from others' lists** — you stop appearing in other people's follower/following lists.

These are real server-side settings on Instagram's internal API. They persist across sessions and devices — this script just flips them.

## Setup

Python 3.10+ and one dependency:

```
pip install requests
```

## Usage

```
python hide_following.py
```

It will ask for your Instagram `sessionid`. To get it:

1. Log into instagram.com in your browser.
2. Open a cookie editor extension (e.g. [Cookie Editor](https://cookie-editor.com)).
3. Find the cookie named `sessionid` and copy its value.
4. Paste it into the script.

Your session ID is only used for the API calls and is not stored anywhere.

## How it works

Instagram has a `SetBooleanSetting` GraphQL mutation that accepts `hide_followers_following_list` and `hide_self_from_others_lists` as setting IDs. The official app doesn't expose these in the UI, but they work and are enforced server-side.

The script authenticates using the same bearer token format the Android app uses, calls the mutation, and prints the result.

## License

MIT
