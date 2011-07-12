!SLIDE
# Option 2

!SLIDE
# Build a mock into the library

!SLIDE
# The Mock
    @@@ruby
    class User
      def self.enable_mock!
        @users = {}
        def self.get(id)
          new(@users[id])
        end

        def self.create(attrs)
          new(@users[next_id] = attrs)
        end
      end
    end

!SLIDE
# The Test
    @@@ruby
    describe "with a user" do
      it "finds it" do
        User.create(:name => "Foo")
        u = User.get(1)
        u.name.should == "Foo"
      end
    end
