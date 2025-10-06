class HRDepartment:
    def __init__(self):
        self._company_name = ""
        self._employee_count = 0
        self._monthly_production_norm = 0.0
        self._hourly_rate = 0.0
        self._income_tax_rate = 0.0

    # Свойства только для записи (write-only)
    def set_company_name(self, name):
        self._company_name = name

    def set_employee_count(self, count):
        self._employee_count = count

    def set_monthly_production_norm(self, norm):
        self._monthly_production_norm = norm

    def set_hourly_rate(self, rate):
        self._hourly_rate = rate

    def set_income_tax_rate(self, tax_rate):
        self._income_tax_rate = tax_rate

    # Метод для подсчета общей выплаты по подоходному налогу
    def calculate_total_income_tax(self):
        return (self._monthly_production_norm *
                self._hourly_rate *
                self._employee_count *
                (self._income_tax_rate / 100.0))


# Функция для безопасного ввода чисел
def input_number(prompt, data_type):
    while True:
        try:
            value = data_type(input(prompt))
            return value
        except ValueError:
            print("Введите корректное число!")


# Демонстрация работы класса
if __name__ == "__main__":
    hr = HRDepartment()

    print("Введите данные для департамента")
    print("=== Ввод данных ===\n")

    name = input("Введите имя: ")
    hr.set_company_name(name)

    hr.set_employee_count(input_number("Введите количество участников: ", int))
    hr.set_monthly_production_norm(input_number("Введите норму времени (часы): ", float))
    hr.set_hourly_rate(input_number("Введите зарплату в час: ", float))
    hr.set_income_tax_rate(input_number("Введите налог (%): ", float))

    print("\nОбщая выплата по подоходному налогу:")
    print(f"{hr.calculate_total_income_tax():.2f}")
