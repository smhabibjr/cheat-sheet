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

## rails g

````ruby
rails generate model User username:string password:string
````

## Routes
````bsh
rake routes | grep products
````



## If gem does not install normaly Try using this way
1. Start  `cmd` terminal and run `ridk`

2. From that cmd, run `gem install mysql2 --platform=ruby -- --with-mysql-dir=c:/your/path/to/Ruby27-x64/msys64/mingw64`
   
   * Make sure that you specify the right path to Ruby installed in your computer
