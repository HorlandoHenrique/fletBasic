import flet as ft

def main(page: ft.Page):
    page.title = "ToDo List Simples"
    page.scroll = ft.ScrollMode.AUTO
    page.vertical_alignment = ft.MainAxisAlignment.START

    input_tarefa = ft.TextField(label="Digite uma tarefa", width=300)
    lista_tarefas = ft.Column()

    def adicionar_tarefa(e):
        if input_tarefa.value.strip() == "":
            return

        nova_tarefa = ft.Checkbox(label=input_tarefa.value)
        lista_tarefas.controls.append(nova_tarefa)

        input_tarefa.value = ""
        page.update()

    botao_adicionar = ft.ElevatedButton(text="Adicionar", on_click=adicionar_tarefa)

    page.add(
        ft.Row(controls=[input_tarefa, botao_adicionar]),
        lista_tarefas
    )

ft.app(target=main)
