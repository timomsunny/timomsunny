import random

class Bank:
    def __init__(self, name, employees, interest_rate):
        self.name = name
        self.employees = employees
        self.interest_rate = interest_rate

    def deposit(self, amount):
        raise NotImplementedError

    def loan(self, amount):
        raise NotImplementedError

    def invest(self, amount):
        raise NotImplementedError

    def analyze_loan(self):
        raise NotImplementedError

    def invest_bonds(self, amount):
        raise NotImplementedError

    def update_interest_rate(self):
        self.interest_rate += random.uniform(-0.5, 0.5)

    def bankrupt(self):
        print("很抱歉，銀行破產了。")
        exit()

class CommercialBank(Bank):
    def __init__(self, name, employees, interest_rate):
        super().__init__(name, employees, interest_rate)
        self.balance = 0
        self.loan = 0

    def deposit(self, amount):
        self.balance += amount
        self.update_interest_rate()

    def loan(self, amount):
        if amount > self.balance * 0.1:
            print("很抱歉，您的貸款額度不能超過目前餘額的 10%。")
        elif self.balance - amount < 0:
            print("很抱歉，您的存款不足以支付貸款。")
        else:
            self.loan += amount
            self.balance -= amount
            self.update_interest_rate()

    def invest(self, amount):
        if amount > self.balance * 0.2:
            print("很抱歉，您的投資額度不能超過目前餘額的 20%。")
        else:
            self.balance -= amount
            self.investment += amount
            self.update_interest_rate()

    def analyze_loan(self):
        if self.loan == 0:
            print("目前沒有貸款。")
        elif self.loan < self.balance:
            print("貸款狀況良好。")
        else:
            print("貸款狀況不佳，請盡快償還。")

    def invest_bonds(self, amount):
        if amount > self.balance * 0.2:
            print("很抱歉，您的投資額度不能超過目前餘額的 20%。")
        else:
            self.balance -= amount
            self.investment += amount
            self.update_interest_rate()

    def bank_run(self):
        if random.random() < 0.05:
            print("發生銀行擠兌！")
            if self.balance < 0:
                self.bankrupt()
            else:
                self.balance -= self.balance * 0.1

class RetailBank(Bank):
    def __init__(self, name, employees, interest_rate):
        super().__init__(name, employees, interest_rate)
        self.balance = 0

    def deposit(self, amount):
        self.balance += amount
        self.update_interest_rate()

    def loan(self, amount):
        if amount > self.balance * 0.5:
            print("很抱歉，您的貸款額度不能超過目前餘額的 50%。")
        elif self.balance - amount < 0:
            print("很抱歉，您的存款不足以支付貸款。")
        else:
            self.balance -= amount
            self.update_interest_rate()

    def invest(self, amount):
        if amount > self.balance * 0.5:
            print("很抱歉，您的投資額度不能超過目前餘額的 50%。")
        else:
            self.balance -= amount
            self.investment += amount
            self.update_interest_rate()

    def analyze_loan(self):
        print("目前零售銀行沒有貸款。")

    def invest_bonds(self, amount):
        if amount > self.balance * 0.5: print("很抱歉，您的投資額度不能超過目前餘額的 50%。")
        else:
            self.balance -= amount
            self.investment += amount
            self.update_interest_rate()

    def bank_run(self):
        if random.random() < 0.1:
            print("發生銀行擠兌！")
            if self.balance < 0:
                self.bankrupt()
            else:
                self.balance -= self.balance * 0.2

class InvestmentBank(Bank):
    def __init__(self, name, employees, interest_rate):
        super().__init__(name, employees, interest_rate)
        self.balance = 0
        self.investment = 0
        self.departments = []

    def deposit(self, amount):
        self.balance += amount
        self.update_interest_rate()

    def loan(self, amount):
        print("投資銀行不提供貸款。")

    def invest(self, amount):
        self.balance -= amount
        self.investment += amount
        self.update_interest_rate()

    def analyze_loan(self):
        print("投資銀行不提供貸款。")

    def invest_bonds(self, amount):
        print("投資銀行不提供債券投資。")

    def add_department(self, department):
        self.departments.append(department)

    def remove_department(self, department):
        self.departments.remove(department)

class Bank:
    def __init__(self, name, employees, interest_rate):
        self.name = name
        self.employees = employees
        self.interest_rate = interest_rate
        self.branches = []

    def deposit(self, amount):
        raise NotImplementedError

    def loan(self, amount):
        raise NotImplementedError

    def invest(self, amount):
        raise NotImplementedError

    def analyze_loan(self):
        raise NotImplementedError

    def invest_bonds(self, amount):
        raise NotImplementedError

    def update_interest_rate(self):
        self.interest_rate += random.uniform(-0.5, 0.5)

    def bankrupt(self):
        print("很抱歉，銀行破產了。")
        exit()

    def add_branch(self, name, employees):
        branch = Branch(name, employees)
        self.branches.append(branch)
        print(f"成功在 {self.name} 開設了新分行 {name}。")
        return branch

class RetailBank(Bank):
    def __init__(self, name, employees, interest_rate):
        super().__init__(name, employees, interest_rate)
        self.balance = 0

    def deposit(self, amount):
        self.balance += amount
        self.update_interest_rate()

    def loan(self, amount):
        if amount > self.balance * 0.5:
            print("很抱歉，您的貸款額度不能超過存款的 50%。")
        else:
            self.balance += amount
            self.update_interest_rate()

    def invest(self, amount):
        print("零售銀行不提供投資服務。")

    def analyze_loan(self):
        if random.random() < 0.2:
            print("很抱

歉，您的貸款未能批准。")
        else:
            print("您的貸款已經批准。")

    def invest_bonds(self, amount):
        print("零售銀行不提供債券投資。")

class CryptoBank(Bank):
    def __init__(self, name, employees, interest_rate):
        super().__init__(name, employees, interest_rate)
        self.balance = 0
        self.crypto_balance = 0

    def deposit(self, amount):
        self.balance += amount
        self.update_interest_rate()

    def loan(self, amount):
        print("加密貨幣銀行不提供貸款。")

    def invest(self, amount):
        print("加密貨幣銀行不提供投資服務。")

    def analyze_loan(self):
        print("加密貨幣銀行不提供貸款分析。")

    def invest_bonds(self, amount):
        print("加密貨幣銀行不提供債券投資。")

    def buy_crypto(self, amount):
        self.balance -= amount
        self.crypto_balance += amount

    def sell_crypto(self, amount):
        self.balance += amount
        self.crypto_balance -= amount

class VirtualBank(Bank):
    def __init__(self, name, employees, interest_rate):
        super().__init__(name, employees, interest_rate)
        self.balance = 0

    def deposit(self, amount):
        self.balance += amount
        self.update_interest_rate()

    def loan(self, amount):
        if amount > self.balance * 0.5:
            print("很抱歉，您的貸款額度不能超過存款的 50%。")
        else:
            self.balance += amount
            self.update_interest_rate()

    def invest(self, amount):
        print("虛擬銀行不提供投資服務。")

    def analyze_loan(self):
        if random.random() < 0.2:
            print("很抱歉，您的貸款未能批准。")
        else:
            print("您的貸款已經批准。")

    def invest_bonds(self, amount):
        print("虛擬銀行不提供債券投資。"）

Import random

# 定義加密貨幣的匯率
exchange_rate = {
    'BTC': 50000,
    'ETH': 1500,
    'LTC': 180
}

# 定義銀行持有的加密貨幣和信用貨幣
bank_holdings = {
    'BTC': 100,
    'ETH': 1000,
    'LTC': 500,
    'USD': 100000
}

# 定義銀行是否提供質押貸款
collateral_loan = True

# 隨機模擬加密貨幣匯率變動
for currency, rate in exchange_rate.items():
    change = random.uniform(-0.1, 0.1)  # 匯率變動的範圍為 -10% 到 +10%
    new_rate = rate * (1 + change)
    exchange_rate[currency] = new_rate

# 打印最新的加密貨幣匯率
print('最新的加密貨幣匯率：')
for currency, rate in exchange_rate.items():
    print(f'{currency}: {rate}')

# 隨機模擬銀行的操作
action = random.choice(['buy', 'sell', 'hold'])
currency = random.choice(['BTC', 'ETH', 'LTC'])
amount = random.randint(1, 10)

# 根據銀行的操作和加密貨幣匯率，更新銀行的持有資產
if action == 'buy':
    cost = amount * exchange_rate[currency]
    if bank_holdings['USD'] >= cost:
        bank_holdings[currency] += amount
        bank_holdings['USD'] -= cost
        print(f'銀行購買了 {amount} {currency}，花費 {cost} 美元')
    else:
        print('銀行資金不足，無法購買加密貨幣')
elif action == 'sell':
    if bank_holdings[currency] >= amount:
        revenue = amount * exchange_rate[currency]
        bank_holdings[currency] -= amount
        bank_holdings['USD'] += revenue
        print(f'銀行出售了 {amount} {currency}，收入 {revenue} 美元')
    else:
        print(f'銀行持有的 {currency} 數量不足，無法出售')
else:
    print(f'銀行持有的 {currency} 數量為 {bank_holdings[currency]}')

# 如果銀行提供質押貸款，則隨機模擬一筆貸款
if collateral_loan:
    loan_currency = random.choice(['BTC', 'ETH', 'LTC'])
    loan_amount = random.randint(10, 100)
    loan_rate = random.uniform(0.05, 0.1)  # 貸款利率為 5% 到 10%
    loan_value = loan_amount * exchange_rate[loan_currency]
    collateral_ratio = random.uniform(1.5, 2.0)  # 質押品價值要超過貸款金額的 1.5 到 2 倍
    collateral_value = loan_value * collateral_ratio
    if bank_holdings[loan_currency] >= loan_amount and bank_holdings['USD'] >= loan_value:
        bank_holdings[loan_currency] -= loan_amount
        bank_holdings['USD'] += loan_value
        print(f'銀行發放了一筆 {loan_value} 美元的質押貸款，貸款金額為 {loan_amount} {loan_currency}，利率為 {loan_rate}')
    else:
        print(f'銀行沒有足夠的資源，無法提供質押貸款')

import time

# 定義遊戲時間
game_time = 0

# 定義遊戲速度
speed = 1

# 設置遊戲速度的倍數
speed_multiplier = {
    1: 1,
    2: 2,
    4: 4,
    8: 8
}

# 開始遊戲循環
while True:
    # 根據遊戲速度計算等待時間
    wait_time = 1 / (speed_multiplier[speed])

    # 更新遊戲時間
    game_time += wait_time

    # 打印遊戲時間
    print(f'遊戲時間：{game_time:.2f}')

    # 等待指定時間
    time.sleep(wait_time)

    # 讓玩家選擇遊戲速度
    user_input = input('請選擇遊戲速度（1、2、4、8倍速，或按Enter繼續）：')
    if user_input.isdigit():
        speed = int(user_input)
        print(f'遊戲速度已設置為 {speed_multiplier[speed]} 倍')
    elif user_input == '':
        continue
    else:
        print('無效的輸入，請重新輸入')

import random

# 定義央行利率和銀行影響力的初始值
central_bank_rate = 2.5
bank_assets = 10
bank_branches = 100

# 定義銀行影響力的計算函數
def calculate_bank_influence(assets, branches):
    return assets * branches

# 定義央行利率決策的函數
def make_rate_decision(rate):
    # 隨機選擇一個變化量
    change = random.choice([-0.5, -0.25, 0, 0.25, 0.5])

    # 計算新的利率
    new_rate = rate + change

    # 限制新利率的範圍在0到10之間
    new_rate = max(0, min(10, new_rate))

    return new_rate

# 模擬央行利率決策的過程
for month in range(12):
    # 打印當前央行利率和銀行影響力
    print(f'第{month+1}個月：央行利率為{central_bank_rate:.2f}，銀行影響力為{calculate_bank_influence(bank_assets, bank_branches):.2f}')

    # 讓玩家輸入利率決策
    user_input = input('請輸入利率決策（不變、上升25或50基點、降低25或50基點）：')
    if user_input == '不變':
        change = 0
    elif user_input == '上升25基點':
        change = 0.25
    elif user_input == '上升50基點':
        change = 0.5
    elif user_input == '降低25基點':
        change = -0.25
    elif user_input == '降低50基點':
        change = -0.5
    else:
        print('無效的輸入，利率不變')
        change = 0

    # 計算新的央行利率
    new_rate = make_rate_decision(central_bank_rate + change)

    # 更新央行利率和銀行影響力
    central_bank_rate = new_rate
    bank_influence = calculate_bank_influence(bank_assets, bank_branches)

# 打印最終央行利率和銀行影響力
print(f'最終央行利率為{central_bank_rate:.2f}，銀行影響力為{bank_influence:.2f}')

