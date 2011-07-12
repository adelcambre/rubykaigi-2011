!SLIDE
# The Example
## User Store


!SLIDE
# The server
    @@@ruby
    class Users < Sinatra::Base
      post "/users/" do
        User.create(params[:user]).to_json
      end

      get "/users/:id" do
        User.get(id).to_json
      end
    end

!SLIDE
# The client
    @@@ruby
    class User
      URL = "http://users.example.org/users"
      def self.get(id)
        res = Restclient.get("#{URL}/#{id}")
        new JSON.parse(res)
      end

      def self.create(attrs)
        res = Restclient.post("#{URL}",
                    {:user => attrs}.to_json)
        new JSON.parse(res.body)
      end
    end
