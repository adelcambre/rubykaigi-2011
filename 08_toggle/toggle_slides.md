!SLIDE
# Toggleable!
# 切り替え可能

!SLIDE code
    @@@ruby
    # in spec_helper.rb or equivalent
    if ENV["MOCK_USERS"] == "true"
      User.testing!
    end

!SLIDE
# So what does this gain us?
# どのような利点があるのでしょうか

!SLIDE
# Very fast mocked specs
# モックを使ったspecが速い

!SLIDE command
<pre><code>$ rake spec:mocked
(in /Users/adelcambre/p/ey_sso)
...............................*.....**......
.............................................
.................
Finished in <span class="callout">11.161133 seconds</span>

107 examples, 0 failures, 3 pending
</code></pre>

!SLIDE
# And very thorough integration tests
# 統合テストが徹底
## with a live backend
## バックエンドが本物

!SLIDE command
<pre><code>$ rake spec:unmocked
(in /Users/adelcambre/p/ey_sso)
...............................*.....**......
.............................................
.................
Finished in <span class="callout">411.887547 seconds</span>

107 examples, 0 failures, 3 pending
</code></pre>

!SLIDE
# The tests do not have to change
# テストを弄る必要が無い

!SLIDE
# So Continuous Integration runs both
# だから継続テストで両方走る

!SLIDE command
<code><pre>
$ rake spec:ci
(in /Users/adelcambre/p/ey_sso)
...............................*.....**......
.............................................
.................
Finished in <span class="callout">429.935862 seconds</span>
107 examples, 0 failures, 6 pending
</code></pre>
<pre><code>
(in /Users/adelcambre/p/ey_sso)
...............................*.....**......
.............................................
.................
Finished in <span class="callout">11.421828 seconds</span>
107 examples, 0 failures, 3 pending
rake spec:ci 7:32.42 total
</code></pre>

!SLIDE
# We don't deploy until both suites are green
# 弊社では両方のテストスイートがパスするまではデプロイしません

!SLIDE
# CI Validates the fake
# CI（継続的インテグレーション）でフェイクを認証

!SLIDE
# This gives you composability
# これで組立が可能になります

!SLIDE
# So when writing an app that uses the client
# このクライアントを使ったアプリケーションを書く時には

!SLIDE
# You can toggle the fake on
# フェイクを使い

!SLIDE bullets incremental
# But with a good test suite in the client
# クライアントに良いテストスイートを付ける事で

!SLIDE
# You have verified the fake correct
# フェイクの正当性を証明しました

!SLIDE
# So you rarely need to run without the fake
# フェイクなしで走らせる事はあまりありません

