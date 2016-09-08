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

