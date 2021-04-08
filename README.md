# Zulip forum bot

Someone was trying to use Zulip as a Q&A forum.  Threaded topics make
this possible, but there is still a problem with keeping things
organized.  Inspired by their workaround, this code will:

* When an emoji reaction (such as :check_mark:) is given, it will
  rename the topic of that thread to include the emoji.  Thus, it is
  easy to mark topics as resolved, in progress, etc.

* If your audience doesn't understand threads and comments in existing
  threads, that's annoying.  You can always rename, or you con comment
  with the :scissors: emoji and it will cut it for you.  You still
  need to rename the topic yourself, but this seems to be less
  annoying mouse strokes.


## Installation and invocation

This is currently alpha-quality but it works for its purpose.  If this
is useful comment and it can be improved.

Currently no installation, clone the repository and run
`zulip-forum-bot.py {zuliprc-file}`.  The first argument is the
zuliprc file you can get from the Zulip server.


## Configuration

Currently configuration is via the same `zuliprc` file that is used,
in a `[forum]` section.  As an example:

```
[api]
email=...@zulip.your.domain
key=abcdefghijklmopqrstuvwxyz
site=https://yourrealm.zulip.your.domain
[forum]
users=user3498@zulip.your.domain, userXXXX@zulip.your.domain
streams=forum
emojis=check_mark, question
```

* `streams`: it will only operate on messages in these streams
  (default: `*` which is all streams).
* `users`: it will only operate when these users make the reaction.
  Users go by email, but note that this might be the internal Zulip
  email (which you have to find out somehow...)  (default: all users)
* `emojis`: it will only operate on these reaction emojis.  Use `*`
  for all.  (default: `check_mark`, `question`).


## Development status and maintenance

This is proof of concept but works.  If you find it useful, get in
touch and we can improve it some.