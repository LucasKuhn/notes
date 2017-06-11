```ruby
# MIGRATIONS

class CreateComments < ActiveRecord::Migration[5.0]
  def change
    create_table :comments do |t|
      t.string     :text
      t.references :post, null: false
      t.references :user, null: false
      
      t.timestamps null: false
    end

    add_foreign_key :comments, :posts, column: :post_id
    add_foreign_key :comments, :users, column: :user_id
  end
end

class CreatePosts < ActiveRecord::Migration[5.0]
  def change
    create_table :posts do |t|
      t.string     :text
      t.references :user, null: false

      t.timestamps null: false
    end

    add_foreign_key :posts, :users, column: :user_id
  end
end

# Votes are polymorphic ("multiple forms" or in CS
# a "single interface to entities of different types")
# since they can apply to two different models.
# (Comments and Posts)
class CreateVotes < ActiveRecord::Migration[5.0]
  def change
    create_table :votes do |t|
      t.boolean    :vote
      t.references :user, null: false
      t.references :voteable, polymorphic: :true, null: false

      # The above line gives us two columns in the DB
      # t.integer :voteable_id (primary key of model 
      #                         instance that received 
      #                         the vote)
      # t.string  :voteable_type (class name of the 
      #                           model instance that
      #                           received the vote)
      # 
      # Why do we need :voteable_type?
      # Well, what would happen if we have a Comment
      # and a Post instance that both have an ID
      # of 5?
      #
      # And what is actually "polymorphic" in this situation?
      # Well, it's the model (Comment or Post) that a Vote 
      # instance refers to. Since Vote instances don't know
      # what type they apply to, they only care that the thing that
      # they belong to is "Voteable" (where the model has a
      # "has_many :votes, as: :voteable" association)

      t.timestamps null: false
    end

    add_foreign_key :votes, :users, column: :user_id

  end
end

# Basic user columns (add more information for whatever
# the program needs - password_digest, email, FN, LN, etc)
class CreateUsers < ActiveRecord::Migration[5.0]
  def change
    create_table :users do |t|
      t.string :name

      t.timestamps
    end
  end
end

#MODELS

class User < ApplicationRecord
  has_many :posts
  has_many :comments
  has_many :votes
end

class Comment < ApplicationRecord
  belongs_to :user
  belongs_to :post
  # When a vote is added for a Comment model instance
  # make sure that the instance ID and class name
  # ("Comment") are added to the votes table
  has_many :votes, as: :voteable

  validates :user_id, presence: { message: "must have user_id" }
  validates :post_id, presence: { message: "must have post_id" }
end

class Post < ApplicationRecord
  belongs_to :user
  has_many :comments
  # When a vote is added for a Post model instance
  # make sure that the instance ID and class name
  # ("Post") are added to the votes table
  has_many :votes, as: :voteable

  validates :user_id, presence: { message: "must have user_id" }
end

class Vote < ApplicationRecord
  belongs_to :user
  belongs_to :voteable, polymorphic: :true

  validates :user_id, 
            uniqueness: 
            { 
              scope: [ :voteable_id, :voteable_type ],
              message: "can only vote for a particular object once " 
            },
            presence: { message: "must have user_id" }
end
```
