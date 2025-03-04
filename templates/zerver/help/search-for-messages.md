# Searching for messages

Zulip has a powerful search engine under its hood. Search for messages using
the search bar at the top of the app.

## Basics

Here's an example of a search query in the app:
`stream:design has:link -is:starred new logo`

It searches for messages in the stream `#design` that have a link, that
you haven't starred, and that contain the words `new` and `logo`.

The permalink for that search (web only) will look something like
this:

`https://your-zulip-url/#narrow/stream/123-design/has/link/-is/starred/search/new.20logo`.

As you start typing, Zulip will suggest possible operator completions.
Operators can be used with keywords, or on their own. For example,

* `stream:design logo` will search for the word `logo` within the stream
  `#design`
* `stream:design` will navigate to the stream `#design`

## List of search operators

### Searching stream messages

* `stream:design`: Search within the stream `#design`.
* `stream:design topic:emoji+picker`: Search within the topic `emoji picker`.
* `streams:public`: Search the history of all [public
  streams](/help/change-the-privacy-of-a-stream) in the organization,
  including streams you are not subscribed to.

### Searching private messages

* `is:private`: Search all your private messages.
* `pm-with:ada@zulip.com`: Search 1-on-1 private messages between you and Ada.
* `pm-with:ada@zulip.com,bob@zulip.com`: Search group private messages
  between you, Bob, and Ada.
* `group-pm-with:ada@zulip.com`: Search all group private message
  conversations that include you and Ada, as well as any other users.

### Searching by message sender or message ID

* `sender:ada@zulip.com`: Search messages sent by Ada.
* `sender:me`: [Search messages you've sent](/help/view-messages-sent-by-a-user#view-messages-youve-sent).
* `near:12345`: Show messages around the message with ID `12345`.
* `id:12345`: Show only message `12345`.

### Searching by message characteristics and flags

* `is:alerted`: See [alert words](/help/pm-mention-alert-notifications#alert-words).
* `is:mentioned`: See [mentions](/help/mention-a-user-or-group).
* `is:starred`: See [starred messages](/help/star-a-message).
* `is:resolved`: Search messages in [resolved topics](/help/resolve-a-topic).
* `-is:resolved`: Search messages in [unresolved topics](/help/resolve-a-topic).
* `is:unread`
* `has:link`
* `has:image`
* `has:attachment`

## Excluding messages

Zulip's search operators can be negated, to exclude messages matching
the rule.  For example, `stream:design -is:resolved -has:image` will
match all messages that don't contain an image and were sent to
unresolved topics in the `#design` stream.

## Searching shared history

Zulip's [stream permissions](/help/stream-permissions) model allows
access to the full history of public streams and [private streams with
shared history](/help/stream-permissions), including messages sent
before you joined the stream (or organization) or those sent to public
streams you are not subscribed to.

By default, Zulip searches messages in your history, i.e. the
messages you actually received.  This avoids cluttering search results
with irrelevant messages from public streams you're not interested in.

If you'd like to instead search the organization's shared history, any
query using the `stream:` or `streams:` operators will search all
messages that you have access to in the selected stream(s).  For
example:

* `streams:public keyword` searches for `keyword` in all public
  streams in the organization.
* `streams:public sender:user@example.com` searches for all messages
  sent by the user to any public stream.

## Words and phrases

Most searches consist of a list of operators followed by a list of keywords.

* `new logo`: Search for messages with both `new` and `logo`.
* `"new logo"`: Search for messages with the phrase `"new logo"`.

Zulip does some basic stemming, so `wave` will match `waves` and
`waving`. Keywords are case-insensitive, so `wave` will also match `Wave`.

Emoji are included in searches, so if you search for `octopus` it will
include messages with
<img src="/static/generated/emoji/images-google-64/1f419.png" alt="octopus"
class="emoji-small"/>.


Note that Zulip ignores common words like `a`, `the`, and about 100
others. A quirk in Zulip's current implementation means that if all of your
keywords are ignored, we'll return 0 search results.

## Related articles

* [Configure multi-language search](/help/configure-multi-language-search)
