!SLIDE
# Option 1

!SLIDE
# No mock at all

!SLIDE code
    @@@ruby
    describe "with a user" do
      it "finds it" do
        u = User.create(:name => "Foo")

        u = User.get(u.id)
        u.name.should == "Foo"
      end
    end

!SLIDE
# A good starting place

!SLIDE
# Spin up a development server and start testing

!SLIDE
# Very good coverage

!SLIDE
# Downsides

!SLIDE
# Very slow tests

!SLIDE
# Can't reset state
## You have to teardown everything after every test
