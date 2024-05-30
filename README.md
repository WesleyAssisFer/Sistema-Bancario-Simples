# Sistema-Bancario-Simples
# Deposito, saque e extrato
# 3 saques diarios com limete de R$500,00 por saque
# caso o usuário não tenha saldo em conta, o sistema deve exibir uma mensagem informando 'que não será possível sacar o dinheiro por falta de saldo'
# todos os saques e depositos devem ser armazenados em uma variavel e exibir na operação de extrato.
# No fim da listagem deve ser exibido o saldo atual da conta
# Os valores devem exibir no formato R$ xxx.xx, por exemplo 1500.45 = R$ 1500.45
limite_diario_saque = 3
valor_depositado = 1500
saque = 0

while True:
    print("""\nVocê deseja realizar qual operação?
    [1]Deposito
    [2]Saque
    [3]Extrato
    [0]Sair
    """)
# PARTE DE DEPOSITO
    user = int(input('Escolha uma opção: '))
    if user == 1:
        deposito = int(input('Qual a quantia que você irá inserir: '))
        valor_depositado += deposito
        print(f"""\nExtrato:
        Saldo anterior de R${valor_depositado - deposito:.2f} mais o deposito de R${deposito:.2f}
        Valor total da conta: R${valor_depositado:.2f} """)
# PARTE DE SAQUE
    if user == 2 and limite_diario_saque > 0 and valor_depositado > saque:
        saque = int(input(f'Qual a quantia que deseja sacar?(limete de R$500,00. Total de saques restantes:{limite_diario_saque}): '))
        if saque <= 500 and valor_depositado > saque:
            valor_depositado -= saque
            limite_diario_saque -= 1
            print(f"""Extrato:
                  Saldo anterior de R${valor_depositado + saque}, saque realizado de R${saque:.2f}
                  Valor total da conta: R${valor_depositado:.2f} """)
# SE O VALOR FOR MAIOR QUE 500 
        while saque > 500:
            print('Inserir um valor menor ou igual a R$500,00')
            saque = int(input(f'Qual a quantia que deseja sacar?(limete de R$500,00. Total de saques restantes:{limite_diario_saque}): '))
            valor_depositado -= saque
            limite_diario_saque -= 1
            print(f"""Extrato:
                  Saldo anterior de R${valor_depositado + saque}, saque realizado de R${saque:.2f}
                  Valor total da conta: R${valor_depositado:.2f} """)
# SE O VALOR FOR MAIOR QUE SAQUE
        if saque > valor_depositado and valor_depositado > 0:
            print(f'Você não possui dinheiro para esse saque, seu saldo é R${valor_depositado}')
# SE O SALDO FOR ZERO
        if valor_depositado == 0:
            print(f'Seu saldo é de R$ {valor_depositado}')
            print("""\nVocê deseja realizar qual operação?
                [1]Deposito
                [3]Extrato
                [0]Sair
                """)
            user = int(input('Escolha uma opção: '))
# SE O LIMITE DIARIO ACABOU
    elif user == 2 and limite_diario_saque <= 0 :
        print('\nSeu limete diario de 3 saques acabou'.center(44, '*'))
# EXTRATO
    if user == 3:
        print(f"""Seu extrado:
            SALDO:{valor_depositado}
            LIMITE DE SAQUE:{limite_diario_saque} """)
# SAIR DO BANCO
    if user == 0:
        print("Obrigado por usar o Banco")
        break
        
