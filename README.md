# Spotify API Testing Summary

This project contains API tests for selected Spotify Web API endpoints using **Postman** and **OAuth 2.0 authentication** with dynamic access token management.

## 🔐 Authentication

All endpoints are tested using **OAuth 2.0 Authorization Code Flow**. Access tokens are dynamically fetched and refreshed when expired.

- **Token Type**: Bearer
- **Authorization Flow**: Authorization Code
- **Auto-refresh Token**: Enabled (for supported environments)

## 📌 Tested Endpoints

### 1. `GET /me`
**Description**: Fetch the current user's profile information.

- **Validations**:
  - Status code: `200 OK`
  - Schema validation for user fields (e.g., `id`, `email`, `display_name`)
  - `id` value matches the expected user from token

---

### 2. `GET /search`
**Description**: Search for tracks, artists, albums, and more.

- **Parameters**:
  - `q`: search query (e.g., `eminem`)
  - `type`: comma-separated list of types (e.g., `track,artist`)
  - `limit`: max number of results (default: 20)
  - `offset`: paging offset

- **Validations**:
  - Status code: `200 OK`
  - Response size matches `limit` if specified
  - Response schema adapts based on `type` parameter
  - Query params (`limit`, `offset`) are validated

---

### 3. `POST /playlists/{playlist_id}/tracks`
**Description**: Add tracks to a user’s playlist.

- **Path Param**: `playlist_id` (string)
- **Body**:
  ```json
  {
    "uris": ["spotify:track:1abc...", "spotify:track:2def..."]
  }


🧪 Test Automation in Postman
Each request includes:

Pre-request Scripts to handle dynamic data (e.g., type selection in /search)

Tests Tab Scripts for:

Schema validation using JSON Schema

Query parameter validation

Response structure and content assertions


📁 Collection Structure
Spotify API Collection
    GET /me
    GET /search
    POST /playlists/{playlist_id}/tracks

🔗 References
[Spotify Web API Docs](https://developer.spotify.com/documentation/web-api)
