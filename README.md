rails new blog_post_challenge -d postgresql -T

Initialized empty Git repository in /Users/learnacademy/Desktop/blog_post_challenge/.git/

git remote add origin https://github.com/learn-academy-2022-bravo/full-stack-rails-vicente-and-vanessa.git

rails db:create
Created database 'blog_post_challenge_development'
Created database 'blog_post_challenge_test'
➜  blog_post_challenge git:(main) ✗ bundle add rspec-rails

 blog_post_challenge git:(main) ✗ rails generate rspec:install
      create  .rspec
      create  spec
      create  spec/spec_helper.rb
      create  spec/rails_helper.rb

blog_post_challenge git:(main) ✗ git add .
➜  blog_post_challenge git:(main) ✗ git commit -m "initial commit"

git checkout -b read-functionality 

rails g model Blog title:string content:string
      invoke  active_record
      create    db/migrate/20220428173836_create_blogs.rb
      create    app/models/blog.rb
      invoke    rspec
      create      spec/models/blog_spec.rb
➜  blog_post_challenge git:(read-functionality) ✗ rails db:migrate

rails c

3.0.0 :002 > Blog.create title:'Initial Blog', content:'This is our initial blog
 post.'
  TRANSACTION (0.2ms)  BEGIN
  Blog Create (6.5ms)  INSERT INTO "blogs" ("title", "content", "created_at", "updated_at") VALUES ($1, $2, $3, $4) RETURNING "id"  [["title", "Initial Blog"], ["content", "This is our initial blog post."], ["created_at", "2022-04-28 18:00:38.062260"], ["updated_at", "2022-04-28 18:00:38.062260"]]                      
  TRANSACTION (0.5ms)  COMMIT                                                   
 =>                                                                             
#<Blog:0x000000010797e160                                                       
 id: 1,                                                                         
 title: "Initial Blog",                                                         
 content: "This is our initial blog post.",                                     
 created_at: Thu, 28 Apr 2022 18:00:38.062260000 UTC +00:00,                    
3.0.0 :003 > Blog.create title:'Second Blog', content:'This is our second blog.'

  TRANSACTION (0.2ms)  BEGIN
  Blog Create (0.4ms)  INSERT INTO "blogs" ("title", "content", "created_at", "updated_at") VALUES ($1, $2, $3, $4) RETURNING "id"  [["title", "Second Blog"], ["content", "This is our second blog."], ["created_at", "2022-04-28 18:03:23.320658"], ["updated_at", "2022-04-28 18:03:23.320658"]]                             
  TRANSACTION (0.3ms)  COMMIT                                                   
 =>                                                                             
#<Blog:0x0000000107984d58                                                       
 id: 2,                                                                         
 title: "Second Blog",                                                          
 content: "This is our second blog.",                                           
 created_at: Thu, 28 Apr 2022 18:03:23.320658000 UTC +00:00,                    
 updated_at: Thu, 28 Apr 2022 18:03:23.320658000 UTC +00:00>                    
3.0.0 :004 > Blog.create title:'Blog 3', content:'This is our third blog.'
  TRANSACTION (0.2ms)  BEGIN
  Blog Create (0.4ms)  INSERT INTO "blogs" ("title", "content", "created_at", "updated_at") VALUES ($1, $2, $3, $4) RETURNING "id"  [["title", "Blog 3"], ["content", "This is our third blog."], ["created_at", "2022-04-28 18:03:55.707032"], ["updated_at", "2022-04-28 18:03:55.707032"]]                                   
  TRANSACTION (0.6ms)  COMMIT                                                   
 =>                                                                             
#<Blog:0x000000010798eec0                                                       
 id: 3,                                                                         
 title: "Blog 3",                                                               
 content: "This is our third blog.",                                            
 created_at: Thu, 28 Apr 2022 18:03:55.707032000 UTC +00:00,                    
 updated_at: Thu, 28 Apr 2022 18:03:55.707032000 UTC +00:00>                    
3.0.0 :005 > Blog.all
  Blog Load (0.6ms)  SELECT "blogs".* FROM "blogs"
 =>                                                         
[#<Blog:0x00000001313e86e0                                  
  id: 1,                                                    
  title: "Initial Blog",                                    
  content: "This is our initial blog post.",                
  created_at: Thu, 28 Apr 2022 18:00:38.062260000 UTC +00:00,
  updated_at: Thu, 28 Apr 2022 18:00:38.062260000 UTC +00:00>,
 #<Blog:0x00000001313e8578                                  
  id: 2,                                                    
  title: "Second Blog",                                     
  content: "This is our second blog.",                      
  created_at: Thu, 28 Apr 2022 18:03:23.320658000 UTC +00:00,
  updated_at: Thu, 28 Apr 2022 18:03:23.320658000 UTC +00:00>,
 #<Blog:0x00000001313e8488                                  
  id: 3,
  title: "Blog 3",
  content: "This is our third blog.",
  created_at: Thu, 28 Apr 2022 18:03:55.707032000 UTC +00:00,
  updated_at: Thu, 28 Apr 2022 18:03:55.707032000 UTC +00:00>] 
3.0.0 :006 > exit
➜  blog_post_challenge git:(read-functionality) ✗ rails g controller Blog
      create  app/controllers/blog_controller.rb
      invoke  erb
      create    app/views/blog
      invoke  rspec
      create    spec/requests/blog_spec.rb
      invoke  helper
      create    app/helpers/blog_helper.rb
      invoke    rspec
      create      spec/helpers/blog_helper_spec.rb
➜  blog_post_challenge git:(read-functionality) ✗ rails db:migrate
➜  blog_post_challenge git:(read-functionality) ✗ rails s
=> Booting Puma
=> Rails 7.0.2.4 application starting in development 
=> Run `bin/rails server --help` for more startup options
Puma starting in single mode...
* Puma version: 5.6.4 (ruby 3.0.0-p0) ("Birdie's Version")
*  Min threads: 5
*  Max threads: 5
*  Environment: development
*          PID: 27691
* Listening on http://127.0.0.1:3000
* Listening on http://[::1]:3000
Use Ctrl-C to stop
Started GET "/" for ::1 at 2022-04-28 11:37:19 -0700
  ActiveRecord::SchemaMigration Pluck (0.6ms)  SELECT "schema_migrations"."version" FROM "schema_migrations" ORDER BY "schema_migrations"."version" ASC
Processing by Rails::WelcomeController#index as HTML
  Rendering /Users/learnacademy/.rvm/gems/ruby-3.0.0/gems/railties-7.0.2.4/lib/rails/templates/rails/welcome/index.html.erb
  Rendered /Users/learnacademy/.rvm/gems/ruby-3.0.0/gems/railties-7.0.2.4/lib/rails/templates/rails/welcome/index.html.erb (Duration: 1.0ms | Allocations: 742)
Completed 200 OK in 9ms (Views: 3.7ms | ActiveRecord: 0.0ms | Allocations: 7012)


^C- Gracefully stopping, waiting for requests to finish
=== puma shutdown: 2022-04-28 11:37:34 -0700 ===
- Goodbye!
Exiting
