!SLIDE
# Back to testing
# テストに話を戻しましょう。

!SLIDE
# Some terminology
# 用語の確認

!SLIDE bullets incremental
# Mock
# モック
* Objects that act like the real thing
* 本物の様に振る舞うオブジェクト
* But with <span class="callout">expectations</span> on the calls made
* 但しどのメソッドが呼び出されるか知っている物

!SLIDE code
    @@@ruby
    it "works" do
      user = mock("user")
      user.should_receive(:send_email).once
      user.process_upgrade
    end

!SLIDE bullets incremental
# Stub
# スタブ
## Replacing certain methods on an object with dummy data
## オブジェクトに定義されているメソッドを仮のデータで置き換える物

!SLIDE code
    @@@ruby
    it "works" do
      user.stub!(:name).and_return("Andy")

      user.greeting.should == "Hello Andy"
    end

!SLIDE
# Fake
# フェイク
## A replacement object that behaves like the real thing, but isn't suitable for production
## 本物の様に振る舞う代替のオブジェクトだが、本番には使えない物

!SLIDE
# Example: an in memory sqlite database
# 例: メモリに格納されているsqliteデータベース

!SLIDE
# People tend to refer to all of these as <span class="callout">"mocks"</span>
# これら全てを「モック」と呼ぶ人も多いです

!SLIDE
# Hence the title of my talk
# それで演題にも「モック」という言葉を使いました

!SLIDE
# This talk is actually about <span class="callout">fakes</span>
# でも、ここではフェイクの話をします。

