---
title: InspIRCd Spanning Tree Protocol &mdash; Messages
---

{! server/_dev.md !}

## Syntax

Messages are formatted the same as [a standard IRCv3 message](https://ircv3.net/specs/extensions/message-tags.html#format) other than the following differences:

- The prefix will be [a SID or UUID](/server/concepts/#uuids) instead of a nick!user@host mask. If no prefix is present then the message is from the directly connected server.
- Lines are terminated with a line feed (`\n`) instead of a carriage return and a line feed (`\r\n`).
- Support for arbitrary message tags is assumed and does not require negotiating a client capability.
- Tags that begin with a tilde (`~`) are internal to the server protocol and are not intended to be exposed to users.
- Once fully authenticated there are no message length limits.

## Messages

This page only lists server messages. For details on user commands that may be sent across the network see the core commands page ([v4 docs](/4/commands), [v3 docs](/3/commands)) or for a specific module please refer to the appropriate page for that module ([v4 docs](/4/modules), [v3 docs](/3/modules)).

<table markdown="1">
<thead>
<tr>
<th>Name</th>
<th>Syntax</th>
</tr>
</thead>
{% for msg in server_messages -%}
{% if msg.source is defined %}
{% set prefix = ":<" ~ msg.source ~ ">" %}
{% else %}
{% set prefix = "[:<sid>]" %}
{% endif %}
<tr markdown="1">
<td markdown="1">[{{ msg.name }}](/server/messages/{{ msg.name | lower }}/)</td>
{% if msg.syntax is not defined %}
<td markdown="1">`{{ prefix }} {{ msg.name }}`</td>
{% elif msg.syntax.text is string %}
<td markdown="1">`{{ prefix }} {{ msg.name }} {{ msg.syntax.text }}`</td>
{% else %}
<td markdown="1">{% for syntax in msg.syntax.text %}`{{ prefix }} {{ msg.name }} {{ syntax }}`{% if not loop.last %}<br>{% endif %}{% endfor %}</td>
{% endif %}
</tr>
{% endfor %}
</tbody>
</table>
