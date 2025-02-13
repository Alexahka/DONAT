<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>A.N.A Donation App</title>
</head>
<body>
    <!-- Заголовок -->
    <h1 style="text-align: center;">Добро пожаловать в A.N.A!</h1>

    <!-- Описание -->
    <p style="text-align: center;">Мы работаем ради лучшего будущего планеты. Помогите нам!</p>

    <!-- Кнопки для пожертвований -->
    <div style="text-align: center;">
        <button onclick="donate(10)">\$10</button>
        <button onclick="donate(25)">\$25</button>
        <button onclick="donate(50)">\$50</button>
        <button onclick="donate(100)">\$100</button>
    </div>

    <!-- Кнопка для другой суммы -->
    <div style="text-align: center; margin-top: 10px;">
        <button onclick="customDonation()">Другая сумма</button>
    </div>

    <!-- Подтверждение пожертвования -->
    <p id="confirmation" style="text-align: center; margin-top: 20px;"></p>

    <!-- Бегущая строка -->
    <marquee style="margin-top: 20px;" scrollamount="5">
        Спасибо за ваше участие! Каждый вклад помогает изменить мир!
    </marquee>

    <script>
        // Функция для обработки стандартных пожертвований
        function donate(amount) {
            document.getElementById('confirmation').textContent = `Спасибо за ваше пожертвование \$${amount}!`;
        }

        // Функция для обработки пользовательского пожертвования
        function customDonation() {
            const customAmount = prompt("Введите сумму пожертвования:");
            if (customAmount && !isNaN(customAmount) && customAmount > 0) {
                document.getElementById('confirmation').textContent = `Спасибо за ваше пожертвование \$${customAmount}!`;
            } else {
                alert("Пожалуйста, введите корректную сумму.");
            }
        }
    </script>
</body>
</html>
