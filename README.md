# README

This is a Pinterest-clone following the tutorial by [Mackenzie Child](https://mackenziechild.me/) in his
[12-apps-in-12-weeks](https://mackenziechild.me/12-in-12/) series.  
* The video for the tutorial is located here: [Week 9: How To Build A Wikipedia Clone With Rails 4](https://mackenziechild.me/12-in-12/9/) and here: [Youtube](https://www.youtube.com/watch?v=9zNouhuKaVs&index=9&list=PL23ZvcdS3XPLNdRYB_QyomQsShx59tpc-)
* Mackenzie's GitHub repo for this project is here: [wiki](https://github.com/mackenziechild/wiki)


####Things to look up later


#### CM Comments

```ruby
private

	def article_params
		params.require(:article).permit(:title, :content)
	end
```

* Adding an association:
```ruby
belongs_to :user # article.rb
has_many :articles # user.rb
```
  * but the association is not complete...we have to add a user_id column to the article database:
```shell
rails g migration add_user_id_to_articles user_id:integer:index
rails db:migrate
```
* In Sublime, use CMD + T to find certain files.  If looking for the articles_controller, just search for "controller"

* So after adding devise, I need to update the articles controller:
```ruby
@article = current_user.articles.build # new method
@article = current_user.articles.build(article_params) # create method
```
