# Humio

This code was brought to you by [BlockFi](https://blockfi.com/), the best way to earn on crypto and grow your wealth.

Humio searches using it's REST API
Supports sync queries and streaming live queries

## TODO: Installation

## Usage

Create a Humio Client

```elixir
client = Humio.Client.new("my-humio-host.com", "my_repo", "my_token")
```

### Query

```elixir
  start = "1s"
  query_string = "#env=dev #type=log foo" # Search all logs in the last second on dev environment that have "foo"
 {:ok, events, state} = Humio.query(client, query_string, start)
```

To only get the events:

```elixir
  start = "1s"
  query_string = "#env=dev #type=log foo"
 events = Humio.query_values(client, query_string, start)
```

### Stream

Turn it into a live query:

```elixir
  start = "1s"
  query_string = "#env=dev #type=log foo"
  event_stream = Humio.stream_values(client, query_string, start)
  last_10_events = event_stream
  |> Enum.take(10)
```
