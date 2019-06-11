## model
enum status: {published: 0, stopped: 1, trading: 2, sold: 3}

view側では
 = f.select :condition, Product.conditionsとして呼び出すことができる