# -Comparador-de-Pre-os-em-Python-
Este é um mini projeto que desenvolvi para facilitar a comparação de preços entre três grandes redes de supermercado Atacadão, Assaí e Mix Mateus. ou qual quer um  so que esse projeto so ta com esse tres link mas pode muda.

# Por que fiz esse projeto?
A ideia surgiu da necessidade de economizar tempo. Em vez de abrir site por site e digitar o nome do produto três vezes, eu criei um script que faz isso com um único comando.

# O que o código faz:
Recebe o nome do produto que eu quero pesquisar (ex: "Arroz 5kg").

Trata o texto para que os links funcionem corretamente (substituindo espaços por +).

Abre automaticamente três abas no navegador padrão com os resultados de busca de cada loja.

# Tecnologias utilizadas:
Python 3

Biblioteca webbrowser: Para integrar o código com o navegador.

Biblioteca time: Para dar um pequeno intervalo entre a abertura das abas.


# Como rodar:
Certifique-se de ter o Python instalado.

Clone o repositório.

Execute o arquivo: python buscador.py

Digite o produto e veja a mágica acontecer!

# ===================== AQUI ESTA O CODIGO DE COMPARAÇÃO DE PREÇO ==================================================================================
import webbrowser
import time


def buscar_precos(produto):
    print(f"--- Iniciando pesquisa para: {produto} ---")

    # Formatando o termo de busca (trocando espaços por + ou %20 para a URL aceitar)
    termo_busca = produto.replace(" ", "+")

    # Dicionário com os links de busca de cada mercado
    # Nota: Alguns sites usam padrões diferentes de URL
    sites = {
        "Atacadão": f"https://www.atacadao.com.br/busca?termo={termo_busca}",
        "Assaí": f"https://www.assai.com.br/busca?q={termo_busca}",
        "Mix Mateus": f"https://www.mateusmais.com.br/busca?termo={termo_busca}"
    }

    # Percorre o dicionário e abre cada link no navegador
    for mercado, link in sites.items():
        print(f"Abrindo busca no {mercado}...")
        webbrowser.open(link)
        time.sleep(2)  # Pequena pausa de 1 segundo para não travar o navegador

    print("\nBusca concluída! Confira as abas no seu navegador.")


# --- Interface do Usuário ---
print("==============================")
print("   COMPARADOR DE PREÇOS v1.0  ")
print("==============================")

item = input("Qual produto você quer comparar hoje? ")
buscar_precos(item)
