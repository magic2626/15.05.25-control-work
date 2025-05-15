# 15.05.25-control-work
Контрольная работа ИЭ-72  за 15.05.25



import flet as ft


def main(page: ft.Page):
    # Настройки страницы
    page.title = "Счётчик кликов"
    page.vertical_alignment = ft.MainAxisAlignment.CENTER
    page.horizontal_alignment = ft.CrossAxisAlignment.CENTER
    page.theme_mode = ft.ThemeMode.LIGHT

    # Переменная для хранения количества кликов
    click_count = 0

    # Элементы интерфейса
    count_text = ft.Text(value="0", size=40, weight=ft.FontWeight.BOLD)

    def increment_click(e):
        nonlocal click_count
        click_count += 1
        count_text.value = str(click_count)
        page.update()

    def reset_clicks(e):
        nonlocal click_count
        click_count = 0
        count_text.value = "0"
        page.update()


    # Создаём кнопки
    click_button = ft.ElevatedButton(
        "Кликнуть!",
        on_click=increment_click,
        width=200,
        height=50,
        color = ft.colors.WHITE,
        bgcolor = ft.colors.GREEN
)

    reset_button = ft.ElevatedButton(
        "Сбросить",
        on_click=reset_clicks,
        width=200,
        height=50,
        color=ft.colors.WHITE,
        bgcolor=ft.colors.RED
    )



    # Добавляем элементы на страницу
    page.add(
        ft.Column(
            [
                ft.Text("Счётчик кликов", size=30),
                count_text,
                click_button,
                reset_button,

            ],
            horizontal_alignment=ft.CrossAxisAlignment.CENTER,
            spacing=20
        )
    )


# Запуск приложения
ft.app(target=main)



