# Sistema de Consulta de Limites - ByteBank
# Desenvolvido para automação e validação de dados de clientes

def consultar_limite(clientes, codigo_consulta):
    """
    Função para consultar o limite de um cliente a partir do dicionário.
    Retorna a string formatada conforme as regras do desafio.
    """
    if codigo_consulta in clientes:
        return f"limite {clientes[codigo_consulta]}"
    else:
        return "cliente nao encontrado"

def main():
    clientes = {}

    print("--- Sistema de Consulta ByteBank ---")
    print("Digite os dados de 3 clientes (Código e Limite separados por espaço, ex: '101 5000'):")
    
    # Leitura dos três cadastros de clientes
    for i in range(3):
        try:
            entrada = input(f"Cadastro {i+1}: ").split()
            if len(entrada) == 2:
                codigo, limite = entrada[0], int(entrada[1])
                # Armazena no dicionário (atualiza se o código já existir)
                clientes[codigo] = limite
        except ValueError:
            print("Valor inválido. Certifique-se de digitar o código e um número inteiro para o limite.")

    # Leitura do código a ser consultado
    codigo_consulta = input("\nDigite o código que deve ser consultado: ").strip()

    # Consulta e exibição do resultado
    resultado = consultar_limite(clientes, codigo_consulta)
    print("\nSaída:")
    print(resultado)

if __name__ == "__main__":
    main()