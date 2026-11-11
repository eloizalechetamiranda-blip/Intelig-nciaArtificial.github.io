import os from openai import OpenAI

==========================================
NOVAAI - INTELIGÊNCIA ARTIFICIAL
==========================================

class NovaAI:

def __init__(self):
    self.nome = "NovaAI"
    self.historico = []

    chave = os.getenv("OPENAI_API_KEY")

    if not chave:
        raise ValueError(
            "Configure a variável OPENAI_API_KEY."
        )

    self.client = OpenAI(api_key=chave)

def responder(self, pergunta):

    try:
        self.historico.append({
            "role": "user",
            "content": pergunta
        })

        resposta = self.client.responses.create(
            model="gpt-4.1-mini",
            instructions="""
            Você é a NovaAI, uma inteligência artificial
            avançada, educada, inteligente e prestativa.

            Suas funções são:
            - Responder perguntas.
            - Criar textos.
            - Ensinar matérias.
            - Ajudar com programação.
            - Desenvolver ideias.
            - Resolver problemas.
            - Auxiliar em projetos.

            Responda sempre em português,
            de maneira clara e organizada.
            """,
            input=self.historico
        )

        texto = resposta.output_text

        self.historico.append({
            "role": "assistant",
            "content": texto
        })

        return texto

    except Exception as erro:
        return f"Erro na NovaAI: {erro}"

def limpar_memoria(self):
    self.historico = []
    return "Memória da conversa limpa!"

def iniciar(self):

    print("=" * 50)
    print("          NOVAAI - SUA INTELIGÊNCIA")
    print("=" * 50)
    print("Olá! Eu sou a NovaAI.")
    print("Estou pronta para ajudar você!")
    print("\nComandos:")
    print("/sair - Encerrar")
    print("/limpar - Limpar memória")
    print("=" * 50)

    while True:

        pergunta = input("\nVocê: ").strip()

        if not pergunta:
            continue

        if pergunta.lower() == "/sair":
            print("\nNovaAI: Até logo!")
            break

        if pergunta.lower() == "/limpar":
            print(self.limpar_memoria())
            continue

        print("\nNovaAI: ", end="", flush=True)

        resposta = self.responder(pergunta)

        print(resposta)

==========================================
EXECUÇÃO DO PROGRAMA
==========================================

if name == "main":

try:
    ia = NovaAI()
    ia.iniciar()

except Exception as erro:
    print(f"Não foi possível iniciar: {erro}")
