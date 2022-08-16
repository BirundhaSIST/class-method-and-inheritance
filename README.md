# class-method-and-inheritance
methods of class and type of inheritance

#classmethod staticmethod instancemethod
        
# inheritance
class Movies:
    def __init__(self, name, collection, producer, year):# instance variable
        self.name=name
        self.collection=collection
        self.producer=producer
        self.year=year
        
# multilevel inheritance
class Marvel(Movies):
    collection=800 # class variable
    profit=400
    def __init__(self, name, collection, producer, year):
        super().__init__(name, collection, producer, year)
        

class hollywood(Marvel):
    profit=900
    def __init__(self, name, collection, producer, year, hero):# instance variable
        super().__init__(name, collection, producer, year)
        self.hero=hero

class screen(Movies):
    def __init__(self, name, collection, producer, year, m=[]):
        super().__init__(name, collection, producer, year)
        self.m=m
    def show_m(self):
        for i in self.m:
            print(i.year)
        
    @classmethod
    def change_profit(cls,amount):
        cls.profit=amount
        return cls.profit
    @classmethod
    def data_set(cls,data):
        name, collection, producer, year=data.split(",")
        return cls(name, collection, producer, year)
    @staticmethod
    def release_date(date):
        lis=[2008, 2004, 2010, 2011]
        if date in lis:
            return'True'
        return'False'

    
m1 = hollywood('iron man', 580, 'kevin', 2008, 'stark')
m2 = hollywood('the incredible hulk', 680, 'gale', 2009, 'hulk')
data='thor,700,feige,2011'
m3=screen('iron man 2', 780, 'feige', 2010, [m1, m2])
print(m1.hero)
print(m3.show_m())
