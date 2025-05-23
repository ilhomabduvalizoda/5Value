Импорт модуля: import requests

Модуль requests используется для выполнения HTTP-запросов к API, чтобы получить актуальные данные о курсе валют.

Функция получения курса валют: def get_exchange_rate(): try: response = requests.get("https://api.exchangerate-api.com/v4/latest/RUB") data = response.json() return data['rates']['USD'] except Exception as e: print("Ошибка при получении курса валют:", e) return None

Эта функция отправляет запрос к API и получает актуальный курс рубля по отношению к доллару.

Если запрос успешен, данные преобразуются в формат JSON и возвращается курс доллара.
В случае ошибки (например, из-за проблем с соединением) выводится сообщение об ошибке.
Функция конвертации валют: def convert_rub_to_usd(rubles, exchange_rate): return rubles * exchange_rate

Данная функция принимает сумму в рублях и курс обмена, возвращая эквивалентную сумму в долларах США.

Основная функция: def main(): print("Добро пожаловать в конвертер валют!") exchange_rate = get_exchange_rate()

if exchange_rate is None:
    print("Не удалось получить курс валют. Закрытие программы.")
    return

print(f"Актуальный курс: 1 RUB = {exchange_rate:.2f} USD")

while True:
    try:
        rubles = float(input("Введите сумму в рублях (или 'exit' для выхода): "))
        dollars = convert_rub_to_usd(rubles, exchange_rate)
        print(f"{rubles} RUB = {dollars:.2f} USD")
    except ValueError:
        print("Ввод завершен. Выход из программы.")
        break
Программа приветствует пользователя и получает актуальный курс валют.
Если курс не удалось получить, программа информирует об этом и завершает свою работу.
В цикле while программа запрашивает у пользователя ввод суммы в рублях, производит конвертацию и выводит результат.
Если ввести некорректные данные (например, текст), программа завершает работу.
Проверка запуска программы: if name == "main": main()
