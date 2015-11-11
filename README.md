Extract From Website
====================

This script extracts the weekly deals from pickapart.ca and compares them with a
watchlist defined in the "products-to-look-for" file. If it finds that you
watchlisted items are on sale in the following week it will email you which ones
they are (defined in the "emails" file).

Emails File
-----------

Just list each email address that will receive the email on a separate line.

This file also allows comments

sample:

```
# Comment
user1@domain.com
user2@domain.com
user3@domain.com
```

Products to look for File
-------------------------

Just list each item on a separate line.

This file also allows comments

sample:

```
# Comment
Any Plain Steel Wheels
Car Doors
Hoods
```

Note: It will also find fragments, so:

```
Steel Wheels
```

Will search for anything that contains "Steel Wheels", which includes the first
item on the sample list.

Note: This file is case insensitive.

num_of_cars
-----------

A non version controlled file that only contains the number of cars that meet
the set of requirements that are on the lot.

sample:

```
11
```

This file is populated automatically on script execution, but it is recommended
to create and populate it manually at first (otherwise you will get your first
email which will contain all the cars on the lot that meet the requirements).

Cronjob
-------

Since this website updates its page with new "on sale items" every week on Fridays at ~6pm,
use the following cronjob settings in order to run this:

```bash
0 18 * * 5 /PATH/TO/extract-from-pick-a-part
```

Note: 0 is the minute of the day, 18 is the hour of the day (18 is 6pm), * means
ever any day of the month, * means any month, 5 means Fridays. Therefore the script
runs every Friday at 6pm.

Note: I do not yet know when to update. The example above runs the script once
every minute.

