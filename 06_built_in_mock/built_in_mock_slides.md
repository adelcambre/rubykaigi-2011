!SLIDE
# Option 2

!SLIDE
# Build a mock into the library

!SLIDE
    @@@ruby
    class User
      def self.enable_mock!
        def self.get(id)
          new(@users[id])
        end

        def self.create(attrs)
          new(@users[next_id] = attrs)
        end
      end
    end
