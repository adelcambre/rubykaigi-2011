!SLIDE
# Option 3

!SLIDE
# Build a fake into the library

!SLIDE
# A fake ruby object

!SLIDE
# The Fake
    @@@ruby
    class User
      def self.testing!
        @users = {}
        def self.get(id)
          new(@users[id])
        end

        def self.create(atrs)
          atrs = atrs.merge(:id => next_id)
          new(@users[atrs[:id]] = atrs)
        end
      end
    end

!SLIDE
# The Test
    @@@ruby
    describe "with a user" do
      it "finds it" do
        u = User.create(:name => "Foo")

        u = User.get(u.id)
        u.name.should == "Foo"
      end
    end

!SLIDE fullscreen top light
![](thumbs_up.jpg)
# Getting Better!
<span class="caption flickr">vegaseddie</span>

!SLIDE
# Tests aren't coupled to the implementation

!SLIDE
# The fake is toggleable!

!SLIDE fullscreen top light
![](thumbs_down.jpg)
# Still not great
<span class="caption flickr">atonal</span>

!SLIDE
# Not at HTTP layer

!SLIDE
# Therefore, a lot of code is not tested

!SLIDE
# We can do better

!SLIDE
# Artifice
### http://github.com/wycats/artifice

!SLIDE
# Artifice stubs net/http with a Rack App

!SLIDE
# An entire fake at the http layer

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
