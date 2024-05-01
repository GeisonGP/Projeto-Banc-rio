# Projeto Bancário em Python
# Implementações de operações bancarias básicas

menu = '''
          ===========MENU============
           Informe a opção desejada!

                 [1] Depositar      
                 [2] Sacar          
                 [3] Extrato        
                 [0] Sair   

          ===========================
=>'''

saldo = 0
limite = 500
extrato = ""
numero_saques = 0
LIMITE_SAQUES = 3

while True:
   
    opcao = input(menu)

    if opcao == "1":
        valor = float(input("Informe o valor do depósito, vê se capricha: "))

        if valor >0:
            saldo += valor
            extrato += f"Depósito: R${valor:.2f}\n"

        else:
            print("Erro! Não aceitamos balas como depósito, valor inválido.")

    elif opcao == "2":
        valor = float(input("Informe o valor do saque: "))
        excedeu_saldo = valor > saldo
        excedeu_limite = valor > limite
        excedeu_saques = numero_saques >= LIMITE_SAQUES

        if excedeu_saldo:
            print ("Erro! Se não tem dinheiro não desce pro play, saldo insuficiente.")
      
        elif excedeu_limite:
            print ("Erro! Limite foram quebrados...")

        elif excedeu_saques:
            print ("Erro! Para evitar que você morra na biqueira, limitamos a apenas 3 saques diários.")

        elif valor > 0:
            saldo -= valor
            extrato += f"Saque: R$ {valor:.2f}\n"
            numero_saques += 1

        else:
            print ("Erro! Não recebemos e não damos balas de troco.")

    elif opcao == "3":
        print("\n===============Extrato==============")
        print("Não foram realizadas movimentações" if not extrato else extrato)
        print(f"\nSaldo: R$ {saldo:.2f}")
        Print("=======================================")

    elif opcao == "0":
        break
   
    else:
        print("Erro! Se não sabe ler peça ajuda a um de nossos atendentes.")






