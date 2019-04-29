#Rails5でのjQuery
jQueryを使うと初回ページ読み込みやリロードで動くがページ遷移して該当するページに戻ってくるとjQueryが動かないことがある。
これはgemのturbolinks(ajaxとhistoryAPI)を使ってページ遷移しやすくなる）のが原因となっていてそもそも$(document).ready()が動いていない状態

これを解決するためには
$(document).on('turbolinks:load', function() { });
と記入してあげると良い。