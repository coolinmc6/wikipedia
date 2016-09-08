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
* Adding category model and then association to Articles:
```
rails g model Category name:string
rails db:migrate
rails g migration add_category_id_to_articles category_id:integer
rails db:migrate
```
* add necessary to code each of the models (category.rb and article.rb)

* When updating the 'new' template, if we want users to be able to add the appropriate category, then we need to 
add that to our safe parameters in the articles_controller.rb:
```ruby
def article_params
	params.require(:article).permit(:title, :content, :category_id)
end
```
* Trying to show the category name in the articles show.html.haml file.  I was having trouble getting the name of the 
category given the category_id...here's one solution:
```haml
%h4
	%strong 
		Subject: 
	= Category.find(@article.category_id).name
%p= @article.content
```
* I did the edit and update actions by myself.  So here we go...
  * "edit" in the controller doesn't need any code in the method.  The controller will simply need to look for the 'edit' view 
  that I have created (edit.html.haml)
  * "Update" is different and actually needs code but it is VERY similar to the create action:
```ruby
def update
	if @article.update(article_params) # if checks if update was successful using article_params method
		redirect_to @article # like 'create', if successful, redirect to the updated article page
	else
		render 'edit' # if NOT, render the edit screen again with the changes the user made
	end
end
```
* I had an issue with me trying to delete an item where the confirm showed up multiple times.  I discuss it in this link from
one of my previous projects [pin_board](https://github.com/coolinmc6/pin_board#2500)
  * Open the config/environments/development.rb file:
```ruby
# the default was true
config.assets.debug = false
```
* To eliminate bullets on unordered lists, do this:
```css
ul {
	list-style: none;
}
```





