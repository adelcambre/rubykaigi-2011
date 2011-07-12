!SLIDE
# Back to testing

!SLIDE
# Option 1

!SLIDE
# Fakeweb

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
# Problems?
<span class="flickr caption">quinnanya</span>

!SLIDE
# Reaches around the library to setup state

!SLIDE
# Tests must have intimate knowledge of implementation

