import os

def limpar_tela():
    '''
    Limpa a tela dando melhor visualização para o usuario.
    '''
    sistema = os.name
    if sistema == 'nt':
        os.system('cls')
    else:
        os.system('clear')

def main():
    tarefas = []
    menu(tarefas)

def menu(tarefas):
    '''
    Menu com todas as opções disponiveis no gerenciamento de tarefas.
    '''
    limpar_tela()
    print(""" -- Gerenciamento de Tarefas --

    [1] - Adicionar Tarefas.
    [2] - Listar Tarefas.
    [3] - Remover Tarefas.
    [4] - Marcar Tarefa como concluida.
    [5] - Limpar Tarefas concluidas.
    [6] - Sair.
          """)
    entrada = int(input("\nDigite o que deseja: "))
    match entrada:
        case 1:
            adicionar_tarefa(tarefas)
        case 2:
            exibir_tarefas(tarefas)
        case 3:
            remover_tarefa(tarefas)
        case 4:
            concluir_tarefa(tarefas)
        case 5:
            limpar_concluidas(tarefas)
        case 6:
            limpar_tela()
            print("Programa finalizado.")
            exit()


def adicionar_tarefa(tarefas):
    '''
    Adiciona tarefas no gerenciamento.
    '''
    limpar_tela()
    exibir_tarefas(tarefas, mostrar_menu=False)
    while True:
        adiciona = input("\nDigite a tarefa: ")

        if adiciona == "":
            menu(tarefas)
            break
        else:
            tarefas.append(adiciona)
            print("\nTarefa adicionada.")
            exibir_tarefas(tarefas, mostrar_menu=False)
            print("\n\nDigite enter para voltar ao menu.")


def exibir_tarefas(tarefas, mostrar_menu=True):
    '''
    Mostra as tarefas que foram adicionadas pelo usuario.
    '''
    limpar_tela()
    if not tarefas:
        print("\nNão possue nenhuma tarefa.")
    else:
        print("-- Lista de Tarefas --\n")
        for i, tarefa in enumerate(tarefas, start=1):
            print(f"{i}. {tarefa}")
    if mostrar_menu: #Criei esse parametro para mostrar apenas o print das tarefas nas outras funções entrar dentro do while
        while True:
            try:
                entrada = input("\nDigite enter para voltar ao menu: ")
                if entrada == '':
                    menu(tarefas)
                    break
                else:
                    print("\nDigite uma entrada válida.")
            except ValueError:
                print("\nDigite uma entrada válida.")


def remover_tarefa(tarefas):
    '''
    Remove a tarefa que usuario deseja
    '''
    limpar_tela()
    exibir_tarefas(tarefas, mostrar_menu=False)

    while True:
        item = input("\nDigite o número correspondente a tarefa que deseja excluir: ")

        if item == '':
            menu(tarefas)
            break
        try:
            item = int(item)
            if item < 1 or item > len(tarefas):
                raise ValueError  # Fora do intervalo válido
            del tarefas[item - 1]  # Ajusta o índice para o índice real da lista, pois a lista começa com o indice 1
            limpar_tela()
            print("\nTarefa removida.")
            exibir_tarefas(tarefas, mostrar_menu=False)
            print("\nDigite enter para voltar ao menu.")
        except (ValueError, IndexError):
            print("\nDigite um número válido correspondente a uma tarefa.")

def concluir_tarefa(tarefas):
    '''
    Conclui as tarefas que o usuario deseja
    '''
    limpar_tela()
    exibir_tarefas(tarefas, mostrar_menu=False)

    while True:
        entrada = input("\nDigite o número da tarefa que deseja concluir: ")
        if entrada == '':
            menu(tarefas)
            break
        try:
           entrada = int(entrada)
           if entrada < 1 or entrada > len(tarefas):
                raise ValueError  # Fora do intervalo válido
           antigo = tarefas[entrada - 1]
           tarefas[entrada - 1] = antigo + " - Tarefa concluída."
           limpar_tela()
           print("\nTarefa concluída.")
           exibir_tarefas(tarefas, mostrar_menu=False)
           print("\nDigite enter para voltar ao menu.")
        except (ValueError, IndexError):
            print("\nDigite uma entrada valida.")

def limpar_concluidas(tarefas):
    '''
    Remove todas as tarefas que já foram concluidas
    '''
    #Criei uma lista de compreensão que remove os elementos que contêm a substring " - Tarefa concluida."
    '''
    Como é uma condição simples, optei pela modificação in-place.
    Como usei a mesma lista por referência em todo o codigo, isso evita que tenha inconsistências e bugs que podem ocorrer caso eu reatribuísse uma nova lista para tarefas.
    '''

    tarefas[:] = [tarefas[i] for i in range(len(tarefas)) if " - Tarefa concluída." not in tarefas[i]]
    limpar_tela()
    print("\nTarefas concluidas foram removidas. ")
    exibir_tarefas(tarefas, mostrar_menu=False)
    while True:
        try:
            entrada = input("\nDigite enter para voltar ao menu.")
            if entrada == '':
                menu(tarefas)
                break
            else:
                print("\nDigite uma entrada valida.")
        except ValueError:
            print("\nDigite uma entrada valida.")



if __name__ == '__main__':
    main()
