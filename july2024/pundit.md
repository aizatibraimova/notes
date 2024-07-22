<!-- Pundit -->

## Authentication vs Authorization
- Do you have permission to do these specific actions?(authorization)
- def initialize(user, post)
    * can this user *update* this post?
- by default everything is false, ypu can override in inherited class policy
- rails g pundit:policy Post
- 
```ruby
def resolve
    scope.all
end
```
```ruby
class ApllictaionController 
```
- looks at the action, authorizing the post, we have current_user
- after_action { authorize @post || Post}
- post.author == user
