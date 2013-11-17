Snapcat
=======

A cat-tastic Ruby wrapper for the [Snapchat](http://snapchat.com) private API.
Meow. This gem is designed to give you a friendly Ruby-like interface for
interacting with the Snapchat API.


Installation
------------

Add this line to your application's `Gemfile`:

    gem 'snapcat', '0.0.1'

And then execute:

    $ bundle

Alternatively, install it via command line:

    $ gem install snapcat


Usage
-----

```ruby

### User Auth

# Initialize a user and login
user = Snapcat::User.new('your-username')
user.login('topsecretpassword')

# Initialize a new user, register, and login
user = Snapcat::User.new('your-new-username')
user.register('1990-01-20', 'test@example.com', 'topsecretpassword')


### User Actions

# Block a user
user.block('username-to-block')

# Clear feed
user.clear_feed

# Fetch a user's updates
user.fetch_updates

# Unblock a user
user.unblock('username-to-unlock')

# Update user's email
user.update_email('newemail@example.com')

# Update user's privacy setting
# Two choices:
#   Snapcat::User::Privacy::EVERYONE
#   Snapcat::User::Privacy::FRIENDS
user.update_privacy(Snapcat::User::Privacy::EVERYONE)


### User Data
# Note: must run `fetch_updates` to capture user data

# Examine all raw user data
user.updates

# Examine snaps received
user.snaps_received

# Examine snaps sent
user.snaps_sent

# Examine friends
user.friends


### Friends
friend = user.friends.first

# Delete a friend :(
friend.delete

# Set a friend's display name
friend.set_display_name('Nik Ro')

# Check what type of friend they are
friend.type.confirmed?
friend.type.unconfirmed?
friend.type.blocked?
friend.type.deleted?


### Snaps
snap = user.snaps_received.first

# Get the file data from the snap
snap.media

# Record a screenshot taken
snap.screenshot

# Record a view
snap.view
```


Contributing
------------

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Add tests and make sure they pass
6. Create new Pull Request


Credits
-------

* [Neal Kemp](http://nealke.mp)
* PHP lib
* Python lib

Copyright &copy; 2013 Neal Kemp

Released under the MIT License, which can be found in the repository in `LICENSE.txt`.
