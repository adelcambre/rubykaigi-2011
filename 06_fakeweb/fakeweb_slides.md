!SLIDE
# Option 2
# 選択肢其の弐

!SLIDE
# Stubbing things out
# スタブを使う

!SLIDE
# Method Stubs
# メソッドをスタブにする

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
# 次の段階としては妥当なところ

!SLIDE
# Faster
# 速い

!SLIDE
# Because nothing is tested
# テストしてないから

!SLIDE
# We can do better, even with stubs
# スタブを使っても改善は可能

!SLIDE
# Fakeweb
### https://github.com/chrisk/fakeweb/

!SLIDE
# Stubs for net/http
# net/http に相当するスタブ

!SLIDE
# NOTE: Not a fake
# フェイクでない事に注意
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
# まずますの出来
<span class="flickr caption">mar00ned</span>

!SLIDE
# Testing at HTTP layer
# HTTPレイヤーでのテスト

!SLIDE
# Good coverage of the library
# ライブラリを恙（つつが）なく網羅

!SLIDE fullscreen top
![](thumbs_down.jpg)
# Problems
# 問題点
<span class="flickr caption">quinnanya</span>

!SLIDE
# Reaches around the library to setup state
# ライブラリを無視して初期化

!SLIDE
# Tests do not use the public API for setup
# パブリックAPIを使わずに初期化

!SLIDE
# Tests must have intimate knowledge of implementation
# テストを書く際にFakewebの内部実装を熟知する必要がある

