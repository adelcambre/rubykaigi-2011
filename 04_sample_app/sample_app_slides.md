!SLIDE
    @@@ruby
    class Users < Sinatra::Base
      post "/users/" do
        User.create(params[:user]).to_json
      end

      get "/users/:id" do
        User.get(id).to_json
      end
    end
