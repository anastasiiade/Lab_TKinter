# Лабораторная работа по Tkinter

## Тема: «Создание графического интерфейса с помощью Tkinter»

### Задание 1: Простое окно с кнопкой

```python
import tkinter as tk
from tkinter import messagebox

def on_button_click():
    print("Кнопка была нажата!")
    messagebox.showinfo("Информация", "Привет, Tkinter!")

root = tk.Tk()
root.title("Моя первая программа")
root.geometry("300x200")

button = tk.Button(root, text="Нажми на меня", command=on_button_click)
button.pack(pady=20)

root.mainloop()
```

### Задание 2: Форма ввода данных

```python
import tkinter as tk
from tkinter import messagebox

def submit_form():
    name = name_entry.get()
    age = age_entry.get()
    messagebox.showinfo("Данные", f"Имя: {name}\nВозраст: {age}")

root = tk.Tk()
root.title("Форма ввода")
root.geometry("300x200")

tk.Label(root, text="Имя:").pack()
name_entry = tk.Entry(root)
name_entry.pack()

tk.Label(root, text="Возраст:").pack()
age_entry = tk.Entry(root)
age_entry.pack()

submit_btn = tk.Button(root, text="Отправить", command=submit_form)
submit_btn.pack(pady=10)

root.mainloop()
```

### Задание 3: Простой калькулятор

```python
import tkinter as tk

def calculate(operation):
    try:
        num1 = float(entry1.get())
        num2 = float(entry2.get())
        
        if operation == "+":
            result = num1 + num2
        elif operation == "-":
            result = num1 - num2
        elif operation == "*":
            result = num1 * num2
        elif operation == "/":
            result = num1 / num2
            
        result_label.config(text=f"Результат: {result}")
    except ValueError:
        result_label.config(text="Ошибка ввода!")
    except ZeroDivisionError:
        result_label.config(text="Деление на ноль!")

root = tk.Tk()
root.title("Простой калькулятор")

entry1 = tk.Entry(root, width=10)
entry1.grid(row=0, column=0, padx=5, pady=5)

entry2 = tk.Entry(root, width=10)
entry2.grid(row=0, column=1, padx=5, pady=5)

tk.Button(root, text="+", command=lambda: calculate("+")).grid(row=1, column=0)
tk.Button(root, text="-", command=lambda: calculate("-")).grid(row=1, column=1)
tk.Button(root, text="*", command=lambda: calculate("*")).grid(row=2, column=0)
tk.Button(root, text="/", command=lambda: calculate("/")).grid(row=2, column=1)

result_label = tk.Label(root, text="Результат: ")
result_label.grid(row=3, columnspan=2)

root.mainloop()
```

### Дополнительное задание: Список дел

```python
import tkinter as tk
from tkinter import messagebox

def add_task():
    task = entry.get()
    if task:
        listbox.insert(tk.END, task)
        entry.delete(0, tk.END)
    else:
        messagebox.showwarning("Предупреждение", "Введите задачу!")

def delete_task():
    try:
        selected = listbox.curselection()
        listbox.delete(selected)
    except:
        messagebox.showwarning("Предупреждение", "Выберите задачу для удаления!")

def mark_completed():
    try:
        selected = listbox.curselection()
        task = listbox.get(selected)
        if not task.startswith("✓ "):
            listbox.delete(selected)
            listbox.insert(selected, f"✓ {task}")
            listbox.itemconfig(selected, {'fg': 'gray'})
    except:
        messagebox.showwarning("Предупреждение", "Выберите задачу для отметки!")

root = tk.Tk()
root.title("Список дел")

frame = tk.Frame(root)
frame.pack(pady=10)

entry = tk.Entry(frame, width=40)
entry.pack(side=tk.LEFT, padx=5)

add_btn = tk.Button(frame, text="Добавить", command=add_task)
add_btn.pack(side=tk.LEFT)

listbox = tk.Listbox(root, width=50, height=15)
listbox.pack(pady=10)

button_frame = tk.Frame(root)
button_frame.pack(pady=10)

delete_btn = tk.Button(button_frame, text="Удалить", command=delete_task)
delete_btn.pack(side=tk.LEFT, padx=5)

complete_btn = tk.Button(button_frame, text="Выполнено", command=mark_completed)
complete_btn.pack(side=tk.LEFT)

root.mainloop()
```

## Ответы на вопросы для самоконтроля

1. **Tkinter** - это стандартная библиотека Python для создания графических интерфейсов. Она предоставляет набор инструментов для создания окон, кнопок, полей ввода и других элементов управления.

2. Главное окно приложения создается с помощью `root = tk.Tk()`, где `root` - это переменная, которая будет представлять главное окно.

3. Основные виджеты Tkinter:
   - `Label` - метка для отображения текста
   - `Button` - кнопка
   - `Entry` - поле ввода
   - `Listbox` - список элементов
   - `Checkbutton` - флажок
   - `Radiobutton` - переключатель
   - `Frame` - контейнер для других виджетов

4. События в Tkinter обрабатываются с помощью функций-обработчиков (callback-функций), которые связываются с виджетами через параметр `command` или с помощью метода `bind()` для более сложных событий.

5. Основные методы упаковки виджетов:
   - `pack()` - автоматическое размещение виджетов
   - `grid()` - размещение в табличной структуре
   - `place()` - точное позиционирование по координатам
