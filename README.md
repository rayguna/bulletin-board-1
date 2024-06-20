# bulletin-board-1

Bulletin Board 1 target: https://bulletin-board-1.matchthetarget.com/

Final Target: https://bulletin-board-1.matchthetarget.com/

Lesson: https://learn.firstdraft.com/lessons/136

Video: https://share.descript.com/view/DlxVNV7HMx4

Grading: https://grades.firstdraft.com/resources/f61de55c-519a-431d-aefc-b3d3c38ae4ba

Draft resource generator: https://learn.firstdraft.com/

<hr>
1. We will create a bulletin board. The design is quite simple. It consists of just two tables, Boards and Posts. The relationship is one to many. One board has many posts.

2. Typing bin/dev initially shows a blank page.

3. Generate the Board table using the draft:resource generator rather than the model generator:

- Type: `rails generate draft:resource board name:string`

Here is the output:
```
bulletin-board-1 main % rails generate draft:resource board name:string
      create  app/controllers/boards_controller.rb
      invoke  active_record
      create    db/migrate/20240620160930_create_boards.rb
      create    app/models/board.rb
      create  app/views/boards
      create  app/views/boards/index.html.erb
      create  app/views/boards/show.html.erb
       route  RESTful routes
```

Then, type: `rails generate draft:resource post title:string body:text expires_on:date board_id:integer`

Here is the outpput:

```
bulletin-board-1 main % rails generate draft:resource post title:string body:text expires_on:date board_id:integer
      create  app/controllers/posts_controller.rb
      invoke  active_record
      create    db/migrate/20240620160959_create_posts.rb
      create    app/models/post.rb
      create  app/views/posts
      create  app/views/posts/index.html.erb
      create  app/views/posts/show.html.erb
       route  RESTful routes
      insert  config/routes.rb
```

- Finally, type: `rake db:migrate`

Here is the output:

```
== 20240620160930 CreateBoards: migrating =====================================
-- create_table(:boards)
   -> 0.0015s
== 20240620160930 CreateBoards: migrated (0.0016s) ============================

== 20240620160959 CreatePosts: migrating ======================================
-- create_table(:posts)
   -> 0.0015s
== 20240620160959 CreatePosts: migrated (0.0016s) =============================

Annotated (2): app/models/board.rb, app/models/post.rb
```
(4 min)

4. Navigating to https://musical-zebra-g54j6jv7pwjfvjr5-3000.app.github.dev/posts and https://musical-zebra-g54j6jv7pwjfvjr5-3000.app.github.dev/boards show the built forms.

(7 min) Begin building the interface.

5. Populate tables with `rake sample_data`.

6. (10 min) Start building the html pages.

7. Added the navigation section.

8. Fixed button name in /boards. Fixed title in /posts.

9. Review this link for date formating: https://entrision.com/blog/formatting-dates-in-ruby/

10. This is a tricky assignment because the scripts that were called in the terminal created default pages that have the incorrect formats and routes. Much works are needed to customize them to match the answer. It may have been easier to start out from sctratch.

11. One issue is that we need to redirect the page back to the boards page after adding a post, but initially the added post is not appended. 
12. Format dta ysung the function strftime(). Also refer to strftime.net.

```
<%= a_post.created_at.strftime("%b %e, %Y") %> 
```

13. (25 min) Validation.

14. Add <%validation%> tag to the body of the layours/application.html.erb to trigger warning, as follows.

```
  <body>
    <!--return to the defalt page-->
    <a href="/">Bulletin Board</a>
    
    <hr>

    <div><%=notice%><div>
    <div><%=alert%><div>
    
    <%= yield %>
  </body>
```
