# FastAPI Tutorial

Minimal FastAPI example with an in-memory todo-style items API.

## Project Structure

```text
.
├── src/
│   └── main.py
├── tests/
├── requirements.txt
└── README.md
```

## Features

- `GET /` returns a basic health-style response.
- `POST /items` creates an item in memory.
- `GET /items` lists items with an optional `limit` query parameter.
- `GET /items/{item_id}` returns a single item by index.

## Item Schema

```json
{
  "text": "Buy milk",
  "is_done": false
}
```

## Local Setup

Create and activate a virtual environment, then install the app dependencies:

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install fastapi uvicorn
```

If you want to track dependencies in the repo, update `requirements.txt` with the installed package versions.

## Run the App

Start the development server from the project root:

```bash
uvicorn src.main:app --reload
```

The API will be available at:

- `http://127.0.0.1:8000`
- Interactive docs: `http://127.0.0.1:8000/docs`
- ReDoc: `http://127.0.0.1:8000/redoc`

## Example Requests

Create an item:

```bash
curl -X POST "http://127.0.0.1:8000/items" \
  -H "Content-Type: application/json" \
  -d '{"text":"Buy milk","is_done":false}'
```

List items:

```bash
curl "http://127.0.0.1:8000/items?limit=10"
```

Get a single item:

```bash
curl "http://127.0.0.1:8000/items/0"
```

## Notes

- Data is stored in memory, so restarting the server clears all items.
- `item_id` is the zero-based index of the item in the in-memory list.
