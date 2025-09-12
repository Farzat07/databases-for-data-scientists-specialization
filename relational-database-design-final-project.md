# Video streaming website

## Background story

The effect of social media companies on the moral and political landscape in
our nations is getting stronger day-by-day. A very recent example can be seen in
Nepal, where [the new leader was elected via Discord](https://www.thestreet.com/crypto/policy/nepals-gen-z-picks-new-leader-on-discord-crypto-community-in-shock).

In this example, a company within the hypothetical country of Y wants to start an
alternative to YouTube. This alternative is intended to serve the same function
while keeping the control of the platform in sovereign hands outside the reach
of foreign interests.

### Structure

The information to be recorded is similar to that of YouTube. Entities include Users,
Channels, Playlists, Videos, and Comments.

For users, it might be tempting to use emails or usernames as identities, but both
are susceptible to change, which could cause headaches as foreign keys would need
to be replaced too. Instead, [UUID](https://en.wikipedia.org/wiki/Universally_unique_identifier)s
will be used. The same goes for channels, playlists, and videos. For all of these,
UUIDs make sense as they could be used in the URLs as well. As for comments, UUIDs
are not needed, as a combination of UserID and [Unix timestamp](https://www.unixtimestamp.com/)
is sufficient (both are fixed, and limiting the number of comments of each user to
1 per second is reasonable).

There are many possible relations between the entities. For example, each user must
have one or more channels, while channels must belong to and only one user. The ER
model will contain a comprehensive list of the relations. Note that some advanced
relations, such as the fact that a channel-owner might allow other users to upload
to his channel, will not be included so as to limit the complexity of the project.

Keep in mind that the implementation is intended to be secure and privacy-friendly.
Passwords are only stored as hashes and view histories are only for the user's own
use and deletable on request.
