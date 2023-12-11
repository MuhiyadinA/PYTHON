`python
products = [['Desktop', 799.00, 5], ['Laptop A', 1200.00, 6]]
sales = []

def stock_check():
    print("[Type, Cost, stock]")
    for i in products:
        print(i)

def add_stock():
    data = []
    stock_type = input("Enter product name: ").capitalize()
    check = False
    while not check:
        try:
            cost1 = float(input("Enter Product cost up to 2 Decimal Places: "))
            cost = round(cost1, 2)
            check = True
        except:
            print("Entered value is not in the required format.")

    check_1 = False
    while not check_1:
        try:
            stock = int(input("Enter the amount of stock: "))
            check_1 = True
        except:
            print("Entered value is not in the required format.")

    data.append(stock_type)
    data.append(cost)
    data.append(stock)
    products.append(data)

def addition():
    s_check = False
    q_check = False
    data1 = []
    while not s_check:
        s_type = input("Enter the Stock Type you want to buy: ")

        for i in products:
            if s_type.lower() == i[0].lower():
                s_check = True

                while not q_check:
                    s_quantity = int(input("Enter the quantity for %s you want to buy: " % s_type))
                    if s_quantity > i[2]:
                        print("Max available stock is: %s" % str(i[2]))
                    else:
                        i[2] = i[2] - s_quantity
                        q_check = True
                        break
        if not s_check:
            print("Entered stock does not exist")
        if s_check and q_check:
            data1.append(s_type)
            data1.append(i[1])
            data1.append(s_quantity)
            sales.append(data1)
            break
