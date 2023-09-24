### notes

- users info is stored in

  > /etc/passwd

- group info is in
  > /etc/group
- to group 2 users in the same group, to have access to the same files, in /etc/group
  > developers:x:1003:bob,michael
- to check how a user is set up
  > id [user]
- or
  > grep -i [user] /etc/passwd
- to see the logged in users currently
  > who
- last shows all logged in users
  > last
- the defaults for sudo rights is found under
  > /etc/sudoers - or visudo
