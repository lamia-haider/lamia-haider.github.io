---
layout: post
title:      "Rails Project - Search and Filter"
date:       2021-06-26 06:23:49 +0000
permalink:  rails_project_-_search_and_filter
---


For my Rails project I created a site that would allow potential pet adopters to peruse the animals currently waiting at a pet shelter. 

One roadblock I hit while working on this were the search filters I wanted to implement. I planned to have them on the index site that displays all the current pets, so as to make the search process easier. 

After a while of Googling and trial-and-error, I came across a method I adapted to create a basic filter.

My aim is to filter by pet species, and/or by pet size. 

To grab the data for this securely, strong params are added to PetsController as such:

```
def query_params
		query_params = params[:query]
		query_params ? query_params.permit(:species, :size) : {}
end

```

The above method permits only the species and size variables to be considered when conducting a query.
The scope for the Pet model should look at these query_params to determine what kind of filters are needed.

```
	scope :filtered, ->(query_params) { Pet::Filter.new.filter(self, query_params) }
```

To do this the scope enlists a new class within app/models/pet/filter.rb with the following content:


```
class Pet::Filter

  def filter(scope, query_params)

    if query_params[:species].present?
      scope = scope.where(species: query_params[:species])
    end
    if query_params[:size].present?
      scope = scope.where(size: query_params[:size])
    end

    scope
  end

end
```

The above method compares the selections made in the search filter with traits passed through to query_params.


The following is added to the PetsController:

```
 def index
        @pets = Pet.filtered(query_params)
    end
```

The above provides the view with the necessary array of filtered pets. 



Below is  what is needed in the view for the Pet index. This lets the user pass the query to the pets_path, so that the page gets reloaded with the filtered results.

```
<%= form_for :query, url: pets_path, method: :get do |form| %>


    <div class="field">
        <%= form.label :species %>
        <%= form.select :species, [["Cat", "Cat"], ["Dog", "Dog"]], include_blank: true, selected: params.dig('query', 'species') %>
    </div>
    <div class="field">
        <%= form.label :size %>
        <%= form.select :size, [["Small", "Small"], ["Medium", "Medium"], ["Big", "Big"]], include_blank: true, selected: params.dig('query', 'species') %>
    </div>
    <br>
      <div class="form-submit-button">
        <%= form.submit 'Search', :class => "form-submit-button" %>
        </div>

    </div>

<% end  %>

```
Note that in this example, the filters being used are selected from pre-established values. Having a search bar where the user types in the search term requires a different type of form field ("text_field" instead of "select").





