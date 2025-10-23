
[tpc5a110402.py](https://github.com/user-attachments/files/23098667/tpc5a110402.py)


def criar_turma():
    return []

def inserir_aluno(turma):
    nome = input("Nome do aluno: ")
    id_aluno = input("ID do aluno: ")
    try:
        notaTPC = float(input("Nota do TPC: "))
        notaProj = float(input("Nota do Projeto: "))
        notaTeste = float(input("Nota do Teste: "))
    except ValueError:
        print("As notas devem ser números!")
        return
    aluno = (nome, id_aluno, [notaTPC, notaProj, notaTeste])
    turma.append(aluno)
    print(f"Aluno {nome} inserido!")

def listar_turma(turma):
    if not turma:
        print("A turma está vazia.")
        return
    for aluno in turma:
        nome, id_aluno, notas = aluno
        print(f"ID: {id_aluno} | Nome: {nome} | Notas: {notas}")

def consultar_aluno(turma):
    id_aluno = input("ID do aluno: ")
    for aluno in turma:
        if aluno[1] == id_aluno:
            print(f"Nome: {aluno[0]} | Notas: {aluno[2]}")
            return
    print("Aluno não encontrado.")

def guardar_turma(turma):
    nome_ficheiro = input("Nome do ficheiro: ")
    with open(nome_ficheiro, "wb") as f:
        pickle.dump(turma, f)
    print(" Turma guardada!")

def carregar_turma():
    nome_ficheiro = input("Nome do ficheiro: ")
    try:
        with open(nome_ficheiro, "rb") as f:
            turma = pickle.load(f)
        print("Turma carregada!")
        return turma
    except FileNotFoundError:
        print("Ficheiro não encontrado.")
        return []

def menu():
    print("""
===== MENU =====
1: Criar uma turma
2: Inserir um aluno
3: Listar a turma
4: Consultar aluno por ID
8: Guardar turma
9: Carregar turma
0: Sair
================
""")

def main():
    turma = []
    while True:
        menu()
        op = input("Escolha uma opção: ")
        if op == "1":
            turma = criar_turma()
            print("Nova turma criada com sucesso!")A
        elif op == "2":
            inserir_aluno(turma)
        elif op == "3":
            listar_turma(turma)
        elif op == "4":
            consultar_aluno(turma)
        elif op == "8":
            guardar_turma(turma)
        elif op == "9":
            turma = carregar_turma()
        elif op == "0":
            print("ok saindo")
            break
        else:
            print("Opção inválida.")


main()

