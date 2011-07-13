!SLIDE
# Option 3

!SLIDE
# Artifice
### http://github.com/wycats/artifice

!SLIDE
# Artifice stubs net/http with a Rack App

!SLIDE
    @@@ruby
    class User
      def self.testing!
        Artifice.activate_with(
                   FakeUsers.new)
      end
    end

!SLIDE
    @@@ruby
    class FakeUsers < Sinatra::Base
      @users = {}
      post "/users/" do
        id = next_id
        @users[id] = params[:user].
                          merge(:id => id)
        @users[id].to_json
      end

      get "/users/:id" do
        @users[id].to_json
      end
    end

!SLIDE
# Same test
    @@@ruby
    describe "with a user" do
      it "finds it" do
        u = User.create(:name => "Foo")

        u = User.get(u.id)
        u.name.should == "Foo"
      end
    end

!SLIDE fullscreen top
![](ftw.jpg)
<span class="caption flickr">robboudon</span>

!SLIDE
# Best of both worlds

!SLIDE
# Fake at the Rack layer for best coverage

!SLIDE
# Tests have no knowledge of implementation

!SLIDE
# So now that we have this...
