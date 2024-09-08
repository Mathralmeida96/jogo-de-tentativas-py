import random

def jogo_adivinhacao():
    print('Digite o nível conforme abaixo:\n')
    print('N°1-Fácil - pontuação inicial 30 (10 tentativas e a cada erro se perde 3 pontos)')
    print('N°2-Médio - pontuação inicial 50 (10 tentativas e a cada erro se perde 5 pontos)')
    print('N°3-Dificil - pontuação inicial 100 (5 tentativas e a cada erro se perde 20 pontos)')

    nivel = int(input('Escolha o nível (1, 2 ou 3): '))

    if nivel == 1:
        min_val = 1
        max_val = 20
        tentativas = 10
        pontuacao_inicial = 30
        penalidade = 3

    elif nivel == 2:
        min_val = 1
        max_val = 50
        tentativas = 10
        pontuacao_inicial = 50
        penalidade = 5

    elif nivel == 3:
        min_val = 1
        max_val = 100
        tentativas = 5
        pontuacao_inicial = 100
        penalidade = 20

    else:
        print('Nível inválido!')
        return

    secreto = random.randint(min_val, max_val)
    pontuacao = pontuacao_inicial

    while tentativas > 0:
        try:
            valor = int(input(f'\nAdivinhe o número gerado (entre {min_val} e {max_val}): '))
        except ValueError:
            print("Por favor, insira um número válido.")
            continue

        if valor == secreto:
            print(f'\nParabéns você acertou!: {secreto}')
            print(f'Sua pontuação é de: {pontuacao}')
            break
        else:
            pontuacao -= penalidade
            tentativas -= 1
            if valor < secreto:
                print('\nErrou. O número é maior!')
            else:
                print('\nErrou. O número é menor!')
            if tentativas > 0:
                print(f'Você ainda tem {tentativas} tentativas e sua pontuação é {pontuacao}')
            else:
                print('\nVocê perdeu!!')

    print(f'O número gerado foi: {secreto}')
    input('\nAperte Enter para sair!')

if __name__ == '__main__':
    jogo_adivinhacao()
