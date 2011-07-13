!SLIDE
# Back to testing

!SLIDE
# Some terminology

!SLIDE bullets incremental
# Mock
* Objects that act like the real thing
* But with <span class="callout">expectations</span> on the calls made

!SLIDE code
    @@@ruby
    it "works" do
      user = mock("user")
      user.should_receive(:send_email).once
      user.process_upgrade
    end

!SLIDE bullets incremental
# Stub
## Replacing certain methods on an object with dummy data

!SLIDE code
    @@@ruby
    it "works" do
      user.stub!(:name).and_return("Andy")

      user.greeting.should == "Hello Andy"
    end

!SLIDE
# Fake
## A replacement object that behaves like the real thing, but isn't suitable for production

!SLIDE
# Example: an in memory sqlite database

!SLIDE
# People tend to refer to all of these as <span class="callout">"mocks"</span>

!SLIDE
# Hence the title of my talk

!SLIDE
# This talk is actually about <span class="callout">fakes</span>

