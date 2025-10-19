import random

class Student:
    def __init__(self, name):
        self.name = name
        self.money = 100
        self.happiness = 50
        self.knowledge = 50
        self.days = 0

    def study(self):
        self.knowledge += 10
        self.happiness -= 5
        self.money -= 5
        print(self.name, "учится. Знания выросли, настроение немного упало.")

    def work(self):
        self.money += 20
        self.happiness -= 5
        print(self.name, "поработал и заработал денег.")

    def rest(self):
        self.happiness += 10
        self.money -= 10
        print(self.name, "отдыхает и тратит деньги.")

    def live_day(self):
        self.days += 1
        print("День", self.days)
        if self.money < 20:
            self.work()
        elif self.knowledge < 40:
            self.study()
        else:
            action = random.choice(["study", "rest", "work"])
            if action == "study":
                self.study()
            elif action == "rest":
                self.rest()
            else:
                self.work()
        if self.happiness <= 0:
            print(self.name, "устал и грустит, симуляция остановлена.")
            return False
        if self.days >= 365:
            print(self.name, "прожил год. Итог:", "Деньги:", self.money, "Знания:", self.knowledge, "Настроение:", self.happiness)
            return False
        return True

student = Student("Студент")
while student.live_day():
    pass
