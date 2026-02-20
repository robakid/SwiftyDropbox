# TeamLogRoutes

Routes for the team_log namespace. For Objective-C compatible routes see `DBTeamLogRoutes`.

---

## getEvents

Retrieves team events. If the result's `hasMore` in `GetTeamEventsResult` field is true, call `getEventsContinue` with the returned cursor to retrieve more entries. If `end_time` is not specified in your request, you may use the returned cursor to poll `getEventsContinue` for new events.

Many attributes note 'may be missing due to historical data gap'.

Note that the `file_operations` category and analogous paper events are not available on all Dropbox Business plans. Use `features/get_values` to check for this feature.

**Permission:** Team Auditing.

**Scope:** `events.read`

```swift
func getEvents(
    limit: UInt32 = 1_000,
    accountId: String? = nil,
    time: TeamCommon.TimeRange? = nil,
    category: TeamLog.EventCategory? = nil,
    eventType: TeamLog.EventTypeArg? = nil
) -> RpcRequest<TeamLog.GetTeamEventsResult, TeamLog.GetTeamEventsError>
```

**Parameters:**
- `limit` - The maximal number of results to return per call. Note that some calls may not return `limit` number of events, and may even return no events, even with `has_more` set to true. In this case, callers should fetch again using `getEventsContinue`.
- `accountId` - Filter the events by account ID. Return only events with this account_id as either Actor, Context, or Participants.
- `time` - Filter by time range.
- `category` - Filter the returned events to a single category. Note that category shouldn't be provided together with event_type.
- `eventType` - Filter the returned events to a single event type. Note that event_type shouldn't be provided together with category.

**Returns:** `TeamLog.GetTeamEventsResult` on success, `TeamLog.GetTeamEventsError` on failure.

---

## getEventsContinue

Once a cursor has been retrieved from `getEvents`, use this to paginate through all events.

**Permission:** Team Auditing.

**Scope:** `events.read`

```swift
func getEventsContinue(cursor: String) -> RpcRequest<TeamLog.GetTeamEventsResult, TeamLog.GetTeamEventsContinueError>
```

**Parameters:**
- `cursor` - Indicates from what point to get the next set of events.

**Returns:** `TeamLog.GetTeamEventsResult` on success, `TeamLog.GetTeamEventsContinueError` on failure.
