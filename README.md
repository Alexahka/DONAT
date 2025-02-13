import tkinter as tk
from tkinter import ttk
import threading

class DonationApp:
    def __init__(self, root):
        self.root = root
        self.root.title("A.N.A World Organization Donation")
        self.root.geometry("800x600")
        self.root.configure(bg="#3498db")  # Синий фон
        
        # Бегущая строка
        self.marquee_text = "Спасибо за ваше участие! Каждый вклад помогает изменить мир!"
        self.marquee_label = tk.Label(root, text=self.marquee_text, font=("Arial", 14), bg="#3498db", fg="white")
        self.marquee_label.place(x=0, y=570)
        self.marquee_offset = 800  # Начальная позиция строки
        self.update_marquee()

        # Заголовок
        title_label = tk.Label(root, text="Добро пожаловать в A.N.A!", font=("Arial", 24, "bold"), bg="#3498db", fg="white")
        title_label.pack(pady=20)

        # Описание
        description_label = tk.Label(root, text="Мы работаем ради лучшего будущего планеты. Помогите нам!",
                                     font=("Arial", 16), bg="#3498db", fg="white")
        description_label.pack(pady=10)

        # Кнопки для пожертвований
        button_frame = tk.Frame(root, bg="#3498db")
        button_frame.pack(pady=20)

        amounts = [10, 25, 50, 100]
        for amount in amounts:
            btn = tk.Button(button_frame, text=f"${amount}", font=("Arial", 14), bg="#2ecc71", fg="white",
                            command=lambda a=amount: self.donate(a))
            btn.pack(side=tk.LEFT, padx=10)

        # Кнопка для другого количества
        custom_donation_button = tk.Button(root, text="Другая сумма", font=("Arial", 14), bg="#e74c3c", fg="white",
                                           command=self.custom_donation)
        custom_donation_button.pack(pady=10)

        # Подтверждение пожертвования
        self.confirmation_label = tk.Label(root, text="", font=("Arial", 16), bg="#3498db", fg="white")
        self.confirmation_label.pack(pady=20)

    def update_marquee(self):
        """Обновление позиции бегущей строки"""
        self.marquee_offset -= 2
        if self.marquee_offset <= -len(self.marquee_text) * 12:  # Ширина символа ~12px
            self.marquee_offset = 800
        self.marquee_label.place(x=self.marquee_offset, y=570)
        self.root.after(50, self.update_marquee)

    def donate(self, amount):
        """Обработка стандартных пожертвований"""
        self.confirmation_label.config(text=f"Спасибо за ваше пожертвование ${amount}!")

    def custom_donation(self):
        """Обработка пользовательского пожертвования"""
        custom_amount = tk.simpledialog.askfloat("Пожертвование", "Введите сумму:")
        if custom_amount:
            self.confirmation_label.config(text=f"Спасибо за ваше пожертвование ${custom_amount:.2f}!")


if __name__ == "__main__":
    root = tk.Tk()
    app = DonationApp(root)
    root.mainloop()
