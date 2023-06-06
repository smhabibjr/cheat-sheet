### Rails g command
````ruby
rails generate scaffold Post name:string title:string content:text
````
````ruby
rails destroy scaffold Post
````
````ruby
rails generate model User username:string password:string
````
````ruby
rails generate controller user index show edit update destroy
````
````ruby
rake routes | grep products
````
````ruby
rails db:migrate
````
````ruby
rails db:rollback
````


### head status
````ruby
 if params[:id].present?
      head :ok
    else
      head :not_found
 end
 
 // send json data from controller.
    if error_msg.length > 0
      # then render head not found
      render :status => :not_found, :json => error_msg
      asdfasdf = 1
    else
      success_msg
      # otherwise send ok status
      render json: success_msg
      asdf = 1
    end
````


## If gem does not install normaly Try using this way
1. Start  `cmd` terminal and run `ridk`

2. From that cmd, run `gem install mysql2 --platform=ruby -- --with-mysql-dir=c:/your/path/to/Ruby27-x64/msys64/mingw64`
   
   * Make sure that you specify the right path to Ruby installed in your computer

## rails app debagging
````ruby
<% rise %>
````

## Send more than one parameters to rails index action from php

``:5050/reportgenerator/?user_id=$user_id&branch_id=$hdl[id]``

Routes like this 

``resources :reportgenerator, only: [:index, :create, :edit, :destroy]``

and we can receive those parameters in our rails controller like this 

````ruby
def index
    branch_id = params[:branch_id]
    user_id = params[:user_id]
end
 ````
 
 ### Rails strong parameters
 
 ````ruby
 def client_params
    params.require(:client).permit(:name, :email, :address)
  end
  ````
  ### form object errors in view
  ````ruby
   <% if form.object.errors.any? %>
    <div>
      <% form.object.errors.full_messages.each do |msg| %>
        <div> <%= msg %> </div>
      <% end %>
    </div>
  <% end %>
  ````
