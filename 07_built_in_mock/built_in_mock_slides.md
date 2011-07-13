!SLIDE
# Option 2

!SLIDE
# Build a fake into the library

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
## (more on this soon)

!SLIDE fullscreen top light
![](thumbs_down.jpg)
# Still not great
<span class="caption flickr">atonal</span>

!SLIDE
# Not at HTTP layer

!SLIDE
# Therefore, a lot of code is not tested
