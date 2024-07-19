<!-- Functional Specifications -->

## BiteSafe Functional Specifications
- BiteSafe: A platform that allows you to log your child's meals and reactions to monitor and identify potential food allergies.

## Pain Points
- It's challenging for caregivers to monitor and identify their child's allergies. 

## Proposed Solution
- A platform where caregivers can log their child's meals and reactions to monitor and identify potential food allergies.

## User Stories
### MVP
- As a parent, I want to log the food my child consumes, so that I can track their diet and identify any food-related issues.
- As a parent, I want to log any allergic reactions my child has, so that I can track and manage my child's allergies. 
- As a parent, I want to add new food items to the list, so that I can accurately log all foods my child consumes. 
- As a parent, I want to add new allergy reaction to the list, so that I can accurately log any new types of reactions my child experiences. 
- As a parent, I want to view all logged food entries, so that I can monitor my child's diet over time. 
- As a parent, I want to view all logged allergy reactions, so that I can monitor my child's allergies over time. 

### Reach Goal
- As a parent, I want the app to analyze food and allergy logs, so that I can identify potential correlations between foods and allergic reactions
- As a parent, I want to view the results of the AI analysis, so that I can take actions to mange my child's allergies. 

## Domain Model
### users
```ruby
# - id
# - created_at
# - updated_at
# - email
# - password

class User
    has_many :children
end
```

### children
```ruby
# - id
# - created_at
# - updated_at
# - name
# - dob
# - gender
# - caregiver_id

class Child
    belongs_to :caregiver, class_name: "User"
    has-many :food_logs
    has_many :allergies
end
```
### foods
```ruby
# - id
# - created_at
# - updated_at
# - name
# - category

class Food
    has-many :food_logs
end
```
### Food_logs
```ruby
# - id
# - created_at
# - updated_at
# - food_id
# - child_id
# - date
# - notes

class FoodLog
    belongs_to :child
    belongs_to :food
end
```
### allergies
```ruby
# - id
# - created_at
# - updated_at
# - description
# - severity
# - detected_date
# - notes
# - child_id

class Allergy
    belongs_to :child
end
```
### analysis
```ruby
# - id
# - created_at
# - updated_at
# - child_id
# - allergy_id
# - log_id
# - date
# - findings
# - recommendations

class Analysis
    belongs_to :child
    belongs_to :food_log
    belongs_to :allergy
end
```
## Sketches
![Sketch](sketch.jpeg)