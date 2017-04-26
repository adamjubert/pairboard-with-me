This is the proposal README.

# Pairboard With Me

## MVP
- [ ] New account creation and login
- [ ] Profile editing
- [ ] View Messages
- [ ] View Pairs
- [ ] CRUD Days (availability)

## User Stories


## Workflow
* On 4/23 at 6pm, User1 adds a new Day for 4/24 with the comment "Available 9am - 3pm"
  * User can update comment or delete the Day altogether until 9am on that date.
* On 4/24 at 8am, User2 adds a new Day for 4/24 with no comment
* On 4/24 at 8:30am, User2 adds a new Day for 4/24 with no comment

* On 4/24 at 9am, Rails Job triggers:
  * Creates Pair with User1 & User2 for 4/24
  * Creates Pair with User3 & null for 4/24
  * Cannot update availability. Cannot update pair.
  * Selectable dates are now changed
* On 4/24 at 11am, User4 clicks "Add Me"
  * Updates Pair to include User4
* On 4/24 at 1pm, User5 clicks "Add Me"
  * Creates new Pair with User5 and null
* On 4/24 at 6pm, "Add Me" button is disabled

## Associations
* User
  * has_many days
  * belongs_to pair

* Day
  * belongs_to user

* Pair
  * has_many users

## Sample Job
Date is sent back as '2017-04-26'
today = Time.now.strftime("%Y-%m-%d")

At 0900 every day:
Pair.delete_all
SELECT * FROM days WHERE date = today
Shuffle array, split into subarrays of length 2 (or 1 if odd)
array.each do |sub|
  Pair.new(sub[0].user_id, sub[1].user_id, today)
end

(optional: Messages)
