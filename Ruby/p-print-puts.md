# p,puts, printメソッドの挙動の違い

###print
print 'hello', 'world' => helloworld　改行が生まれない
puts "hello, " "world" => hello, 
                          world　のように改行が生まれる

pは正確な型と共に値を返す
p 100 => 100
p "100" => "100"
puts "100" => 100
puts 100 => 100