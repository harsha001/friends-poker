# Friends Poker

Online Texas Hold'em for friends, as an Android app. Play money only.

## Get the app

Open this repository's **Releases** page on your phone, download `FriendsPoker.apk`, and open it. Android will ask you to allow installs from your browser or file manager the first time.

Every push to `main` builds a new APK automatically (see the **Actions** tab).

## Game server (Firebase)

Tables are stored in a Firebase Realtime Database. The connection details live in `app/src/main/assets/firebase-config.js`.

In the Firebase console, open **Realtime Database → Rules** and publish these rules so tables keep working after the 30-day test mode ends:

```json
{
  "rules": {
    "tables": {
      ".read": true,
      ".write": true,
      ".indexOn": ["updatedAt"]
    }
  }
}
```

## How to play

1. Enter your name and tap **Create table**.
2. Tap **Invite** to send the 4-letter code to friends.
3. Friends open the app, enter their name, and join with the code.
4. The host deals each hand. If a player is away, the host can fold for them.

## Notes

- Cards are stored in the shared game data, so a technically minded player could inspect them. It's built for friendly games.
- The first build creates `app/friendspoker.jks` and commits it. Every later APK is signed with it, so new versions install over old ones. Keep that file.
