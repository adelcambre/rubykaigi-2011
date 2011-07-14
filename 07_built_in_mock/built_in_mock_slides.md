!SLIDE
# Option 3
# 選択肢其の参

!SLIDE
# Build a fake into the library
# フェイクをライブラリに組み込む

!SLIDE
# A fake ruby object
# Rubyオブジェクトであるフェイク

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
# 段々良くなってますね！
<span class="caption flickr">vegaseddie</span>

!SLIDE
# Tests aren't coupled to the implementation
# テストと実装が隔離されています

!SLIDE
# The fake is toggleable!
# フェイクは切り替え可能

!SLIDE fullscreen top light
![](thumbs_down.jpg)
# Still not great
# でもまだ今一つです
<span class="caption flickr">atonal</span>

!SLIDE
# Not at HTTP layer
# テストはHTTPレイヤーではない

!SLIDE
# Therefore, a lot of code is not tested
# だから、テストされていない部分も多い

!SLIDE
# We can do better
# 改善の余地あり

!SLIDE
# Artifice
### http://github.com/wycats/artifice

!SLIDE
# Artifice stubs net/http with a Rack App
# Artifice では本物の Rack アプリケーションを net/http のスタブとして使います

!SLIDE
# An entire fake at the http layer
# http レイヤーは全てフェイク

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
# 先程と同じテストが使えます
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
# イイトコ取り

!SLIDE
# Fake at the Rack layer for best coverage
# Rackレイヤーでフェイクを使い幅広くテスト

!SLIDE
# Tests have no knowledge of implementation
# テストが実装についての知識を必要としない

!SLIDE
# So now that we have this...
# そろそろ本題に入りますか
