!SLIDE
# The Example
# 例
## User Store
## ユーザ

!SLIDE
# The server
# サーバのコード
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
# クライアントのコード
    @@@ruby
    class User
      URL = "http://users.example.org/users"
      def self.get(id)
        res = RestClient.get("#{URL}/#{id}")
        new JSON.parse(res)
      end

      def self.create(attrs)
        res = RestClient.post("#{URL}",
                  {:user => attrs}.to_json)
        new JSON.parse(res.body)
      end
    end
