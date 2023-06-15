Paste this in https://dbdiagram.io/

```ts
Table users {
   id serial [pk, increment]
   created_at timestamp
   updated_at timestamp
   username varchar(30)
   avatar varchar(200)
   bio varchar(400)
   phone varchar(25)
   email varchar(40)
   password varchar(25)
   status varchar(15)
}

Table posts {
   id serial [pk, increment]
   created_at timestamp
   updated_at timestamp
   url varchar(200)
   user_id integer [ref: > users.id]
}

Table comments {
   id serial [pk, increment]
   created_at timestamp
   updated_at timestamp
   contents varchar(240)
   user_id integer [ref: > users.id]
   post_id integer [ref: > posts.id]
}

Table likes {
  id integer [pk, increment]
  created_at timestamp
  user_id integer [ref: > users.id]
  post_id integer [ref: > posts.id]
  comment_id integer [ref: > comments.id]
}

Table photo_tags {
  id integer [pk, increment]
  created_at timestamp
  updated_at timestamp
  user_id integer [ref: > users.id]
  post_id integer [ref: > posts.id]
  x integer
  y integer
}

Table caption_tags {
  id integer [pk, increment]
  created_at timestamp
  user_id integer [ref: > users.id]
  post_id integer [ref: > posts.id]
}

Table hashtags {
  id integer [pk, increment]
  created_at timestamp
  title varchar(20)
}

Table hashtags_posts {
  id integer [pk, increment]
  hashtag_id integer [ref: > hashtags.id]
  post_id integer [ref: > posts.id]
}

Table followers {
  id integer [pk, increment]
  leader_id integer [ref: > users.id]
  follower_id integer [ref: > users.id]
}
```
