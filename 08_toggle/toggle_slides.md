!SLIDE
# Toggleable!

!SLIDE code
    @@@ruby
    # in spec_helper.rb or equivalent
    if ENV["MOCK_USERS"] == "true"
      User.enable_mock!
    end

!SLIDE
# So what does this gain us?

!SLIDE
# Very fast mocked specs

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
## with a live backend

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
# The tests does not have to change

!SLIDE
# So Continuous Integration Runs both

!SLIDE command
<code><pre>
$ rake spec:ci
(in /Users/adelcambre/p/ey_sso)
...............................*.....**......
.............................................
.................
Finished in 429.935862 seconds
107 examples, 0 failures, 6 pending
</code></pre>
<pre><code>
(in /Users/adelcambre/p/ey_sso)
...............................*.....**......
.............................................
.................
Finished in 11.421828 seconds
107 examples, 0 failures, 3 pending
rake spec:ci 7:32.42 total
</code></pre>

!SLIDE
# We don't deploy, until both suites are green
