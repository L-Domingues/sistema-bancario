# sistema-bancario-DIO
Project Challenge: Creating simple banking system

menu = '''
=================================
            BANCO DIO 
=================================
[0] Depósito
[1] Saque
[2] Extrato
[3] Sair
Digite qual operação deseja: '''

saldo = 0
limite = 500
nsaques = 0
limitesaques = 3
extrato = []

while True:
    opcao = int(input(menu))

    if opcao == 0:  #Deposito
        print('-'*33)
        deposito = float(input('Depósito: '))
        while deposito < 0:
            deposito = float(input('Valor inválido. Depósito: '))
        saldo+=deposito
        extrato.append(f'Deposito : R${deposito:.2f}')

    elif opcao == 1: #Saque
        print('-' * 33)
        saque = float(input('Saque: '))
        while not (0 <= saque <= limite) or saque > saldo or nsaques >= limitesaques:
            if not (0 <= saque <=limite):
                saque = float(input('Valor ultrapassa seu limite(R$500,00). Saque: '))
            elif saque > saldo:
                saque = float(input('Saldo insuficiente. Digite um valor dentro do seu saldo: '))
            elif nsaques >= limitesaques:
                print('Saque não finalizado. Limites diários(3) atingidos.')
                break
        else:
            nsaques+=1
            saldo-=saque
            extrato.append(f'Saque: R${saque:.2f}')

    elif opcao == 2: #Extrato
        print('-'*33)
        print('             EXTRATO')
        print('-'*33)
        for unidade in extrato:
            print(unidade)
        print (f'Saldo: {saldo:.2f}')

    elif opcao == 3: #Sair
        break

    else:
        print('Opção inválida. Selecione uma operação válida')

