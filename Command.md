 herokuでのデプロイ
- gem pgがある場合はまずコマンドで`brew install postgresql`でインストールする
  これをせずにbundle installすると下のようなエラーがターミナルで出る
 #terminal
 Fetching pg 1.1.4
Installing pg 1.1.4 with native extensions
Gem::Ext::BuildError: ERROR: Failed to build gem native extension.

    current directory: /Users/ykuma/.rbenv/versions/2.5.1/lib/ruby/gems/2.5.0/gems/pg-1.1.4/ext
/Users/ykuma/.rbenv/versions/2.5.1/bin/ruby -r ./siteconf20190415-44576-wuykxt.rb extconf.rb
checking for pg_config... no
No pg_config... trying anyway. If building fails, please try again with
 --with-pg-config=/path/to/pg_config
checking for libpq-fe.h... no
Can't find the 'libpq-fe.h header
*** extconf.rb failed ***
Could not create Makefile due to some reason, probably lack of necessary
libraries and/or headers.  Check the mkmf.log file for more details.  You may
need configuration options.
