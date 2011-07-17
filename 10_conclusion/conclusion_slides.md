!SLIDE bullets incremental
# Downsides to this pattern?
# このパターンの問題点
* assume unmocked in your tests
* 現存のテストはモックを使っていない事が前提

!SLIDE bullets
# Downsides to this pattern?
# このパターンの問題点
* Have to always clean up state
* テストの度に状態を初期化する必要がある

!SLIDE bullets
# Downsides to this pattern?
# このパターンの問題点
* Unique data conflicts
* ユニークなデータの衝突

!SLIDE
# Next steps
# 次は？

!SLIDE
# Artifice just takes a Rack App
# Artifice では Rack アプリケーションを使います

!SLIDE
# The server code is a Rack App
# サーバは Rack アプリケーションです

!SLIDE
# Why not use the actual server as the mock?
# 実際のサーバをモックとして使えないでしょうか

!SLIDE
# We have done this in a few limited cases
# 限られたケースでは実践済み

!SLIDE
    @@@ruby
    Artifice.activate_with(
      Rack::Builder.new do
        map "#{URL_FOR_EY_SSO}/" do
          run HaxMockMoiApi.new
        end
        map "#{URL_FOR_TRESFIESTAS}/" do
          run Tresfiestas::Application
        end
        map "#{URL_FOR_AWSM}/" do
          run FakeAWSM
        end
        map "#{URL_FOR_LISONJA}/" do
          run Lisonja
        end
        map "#{URL_FOR_SECRET_ADMIN}/" do
          run SecretAdmin
        end
      end


!SLIDE
# Not enough experience to recommend it yet
# まだ経験不足で推奨するほどではない

!SLIDE larger
# Thanks!
## ご静聴有り難うございました

!SLIDE
# Thanks to Hiro Asari
# 日本語字幕は浅里さん
## for Japanese translations

!SLIDE
# Thanks to Scott Chacon
## スコット・シャコーン氏
## for showoff
## showoff の開発者
### https://github.com/schacon/showoff


!SLIDE right
# <span class="callout">Questions?</span>
# 質問などあれば
## http://twitter.com/adelcambre
## http://github.com/adelcambre
## http://flickr.com/adelcambre
