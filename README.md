# Translating Between SQL and ActiveRecord

## Translate from SQL to Active Record

SELECT *
FROM
  users;
`User.all`

SELECT *
FROM
  users
WHERE
  user.id = 1;
`User.where(id: 1)`

SELECT *
FROM
  posts
ORDER BY
  created_at DESC
LIMIT 1;
`Post.first`

SELECT *
FROM
  users
JOIN
  posts
ON
  posts.author_id = users.id
WHERE
  posts.created_at >= '2014-08-31 00:00:00';
`User.joins("JOIN posts p ON p.author_id = users.id").where("p.created_at >= '2014-08-31 00:00:00'")`

SELECT
  count(*)
FROM
  users
GROUP BY
  favorite_color
HAVING
  count(*) > 1;
`User.select('count(*)').group('favorite_color').having('count(*) > 1').length`

* The most recently updated user
`User.order(updated_at: :desc).limit(1)`

* The oldest user (by age)
`User.order(dob: :asc).limit(1)`

* all the users
`User.all`

* all posts sorted in descending order by date created
`Post.order(created_at: :desc)`
