!SLIDE
# Option 2

!SLIDE
# Stubbing things out

!SLIDE
# Method Stubs

!SLIDE code
    @@@ruby
    it "works" do
      user = mock(User)
      User.stub!(:get).with(1).
          and_return(user)
      user.stub!(:name).and_return("foo")

      User.get(1).name.should == "foo"
    end

!SLIDE
# A logical next step

!SLIDE
# Faster

!SLIDE
# Because nothing is tested

!SLIDE
# We can do better, even with stubs

!SLIDE
# Fakeweb
### https://github.com/chrisk/fakeweb/

!SLIDE
# Stubs for net/http

!SLIDE
# NOTE: Not a fake
## Despite the name

!SLIDE
    @@@ruby
    describe "with a user" do
      it "finds it" do
        FakeWeb.register_uri(:get, 
         "http://users.example.org/users/1",
         :body => {:name => "Foo"}.to_json)

        u = User.get(1)
        u.name.should == "Foo"
      end
    end

!SLIDE
    @@@ruby
    it "creates a user" do
      FakeWeb.register_uri(:post,
        "http://users.example.org/users/",
        :body => {:name => "Foo"}.to_json)

      u = User.create(:name => "Foo")
      u.name.should == "Foo"
    end

!SLIDE fullscreen top larger
![](thumbs_up.jpg)
# Not bad
<span class="flickr caption">mar00ned</span>

!SLIDE
# Testing at HTTP layer

!SLIDE
# Good coverage of the library

!SLIDE fullscreen top
![](thumbs_down.jpg)
# Problems
<span class="flickr caption">quinnanya</span>

!SLIDE
# Reaches around the library to setup state

!SLIDE
# Tests do not use the public API for setup

!SLIDE
# Tests must have intimate knowledge of implementation

