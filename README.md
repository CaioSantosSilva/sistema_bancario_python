# sistema_bancario_python
Nesse repositório estou implementando o desafio "Criando um Sistema Bancário com Python" do curso Formação Python Developer na DIO

menu = """

    [d] Depósito
    [s] Saque
    [e] Extrato
    [q] Sair

=> """

saldo = 0
limite = float(input("Informe o limite da conta: "))  # Ajuste para receber o limite como um número float
extrato = ""
numero_saques = 0
LIMITE_SAQUES = 3

while True:

    opcao = input(menu)

    if opcao == "d":
        valor = float(input("Informe o valor do Depósito: "))

        if valor > 0:
            saldo += valor  # Correção para adicionar o valor ao saldo
            extrato += f"Depósito: R$ {valor:.2f}\n"  # Atualização do extrato com o depósito

        else:
            print("Operação falhou! Informe um valor correto")

    elif opcao == "s":
        valor = float(input("Informe o valor do saque: "))
        excedeu_saldo = valor > saldo
        excedeu_limite = valor > limite  # Correção para verificar o limite da conta

        excedeu_saques = numero_saques >= LIMITE_SAQUES

        if valor <= 0:
            print("Operação falhou! Informe um valor válido")

        elif excedeu_saldo:
            print("Operação falhou! Você não tem saldo suficiente")

        elif excedeu_limite:
            print("Operação falhou! O valor do saque excede o limite da conta")

        elif excedeu_saques:
            print("Operação falhou! Excedeu o máximo de saques permitidos")

        else:
            saldo -= valor
            extrato += f"Saque: R$ {valor:.2f}\n"
            numero_saques += 1

    elif opcao == "e":
        print("\n================EXTRATO================")
        print("Não foram realizadas movimentações." if not extrato else extrato)
        print(f"\nSaldo: R$ {saldo:.2f}")
        print("=========================================")

    elif opcao == "q":
        break

    else:
        print("Operação inválida! Por favor, selecione novamente a operação desejada")

