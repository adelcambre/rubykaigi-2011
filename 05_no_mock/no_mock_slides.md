!SLIDE
# Option 1
# 選択肢其の壱

!SLIDE
# No mock at all
# モックを使わない

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
# 初めとしてはまあまあ

!SLIDE
# Spin up a development server and start testing
# 開発サーバを起動してテストを始めましょう

!SLIDE
# Very good coverage
# 高度なコードカバレッジ

!SLIDE
# Downsides
# 問題点

!SLIDE
# Very slow tests
# 遅い

!SLIDE
# Can't reset state
# テストが始まったらオブジェクトの状態を元に戻せない
## You have to teardown everything after every test
## テストの度に全てやり直す必要がある
