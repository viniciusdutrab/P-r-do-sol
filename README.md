# Por-do-sol
aplicativo para pessoas com alzheimer 
import tkinter as tk
from tkinter import messagebox, simpledialog
from datetime import datetime
import time
import random

class AplicativoPordosol:
    def __init__(self, master):
        self.master = master
        self.master.title("Aplicativo Pôr do Sol")
        self.familiares = []

        # Tela inicial
        self.frame_home = tk.Frame(self.master)
        self.frame_home.pack(pady=10)

        # Título
        self.titulo = tk.Label(self.frame_home, text="Bem-vindo ao Aplicativo Pôr do Sol", font=("Arial", 16))
        self.titulo.pack()

        # Botões da tela inicial
        self.botao_identificacao = tk.Button(self.frame_home, text="Identificação de Familiares", command=self.tela_identificacao)
        self.botao_identificacao.pack(pady=5)

        self.botao_atividades = tk.Button(self.frame_home, text="Atividades Lúdicas", command=self.tela_atividades)
        self.botao_atividades.pack(pady=5)

        self.botao_treinamento_memoria = tk.Button(self.frame_home, text="Treinamento de Memória", command=self.tela_treinamento_memoria)
        self.botao_treinamento_memoria.pack(pady=5)

        self.botao_relogio_calendario = tk.Button(self.frame_home, text="Relógio e Calendário", command=self.tela_relogio_calendario)
        self.botao_relogio_calendario.pack(pady=5)

        self.botao_audios_videos = tk.Button(self.frame_home, text="Áudios e Vídeos", command=self.tela_audios_videos)
        self.botao_audios_videos.pack(pady=5)

        self.botao_alertas = tk.Button(self.frame_home, text="Alertas", command=self.tela_alertas)
        self.botao_alertas.pack(pady=5)

    def tela_identificacao(self):
        # Exibe fotos, vídeos e informações dos familiares
        top = tk.Toplevel(self.master)
        top.title("Identificação de Familiares")
        tk.Label(top, text="Identificação de Familiares", font=("Arial", 16)).pack(pady=10)

        # Adiciona familiar (simplificação)
        tk.Button(top, text="Adicionar Familiar", command=self.adicionar_familiar).pack(pady=5)
        tk.Button(top, text="Mostrar Familiares", command=self.mostrar_familiares).pack(pady=5)

    def adicionar_familiar(self):
        nome = simpledialog.askstring("Nome", "Digite o nome do familiar:")
        parentesco = simpledialog.askstring("Parentesco", "Digite o grau de parentesco:")
        idade = simpledialog.askstring("Idade", "Digite a idade do familiar:")

        if nome and parentesco and idade:
            familiar = {"nome": nome, "idade": idade, "parentesco": parentesco}
            self.familiares.append(familiar)
            messagebox.showinfo("Sucesso", f"Familiar {nome} adicionado.")
        else:
            messagebox.showwarning("Erro", "Preencha todos os campos.")

    def mostrar_familiares(self):
        if not self.familiares:
            messagebox.showinfo("Nenhum Familiar", "Nenhum familiar cadastrado.")
        else:
            familiares_info = "\n".join([f"Nome: {f['nome']}, Parentesco: {f['parentesco']}, Idade: {f['idade']}" for f in self.familiares])
            messagebox.showinfo("Familiares", familiares_info)

    def tela_atividades(self):
        # Jogos e atividades cognitivas
        top = tk.Toplevel(self.master)
        top.title("Atividades Lúdicas")
        tk.Label(top, text="Escolha uma atividade", font=("Arial", 16)).pack(pady=10)
        tk.Button(top, text="Associação de Imagens", command=self.jogo_associacao).pack(pady=5)
        tk.Button(top, text="Quebra-cabeça", command=self.jogo_quebra_cabeca).pack(pady=5)

    def jogo_associacao(self):
        # Exemplo de jogo de associação
        messagebox.showinfo("Jogo", "Iniciando jogo de associação...")

    def jogo_quebra_cabeca(self):
        # Exemplo de quebra-cabeça
        messagebox.showinfo("Jogo", "Iniciando quebra-cabeça...")

    def tela_treinamento_memoria(self):
        top = tk.Toplevel(self.master)
        top.title("Treinamento de Memória")
        tk.Label(top, text="Treinamento de Memória", font=("Arial", 16)).pack(pady=10)
        tk.Button(top, text="Sequência de Palavras", command=self.exercicio_sequencia_palavras).pack(pady=5)

    def exercicio_sequencia_palavras(self):
        # Treinamento de sequência de palavras
        messagebox.showinfo("Treinamento", "Iniciando sequência de palavras...")

    def tela_relogio_calendario(self):
        top = tk.Toplevel(self.master)
        top.title("Relógio e Calendário")
        tk.Label(top, text="Relógio e Calendário", font=("Arial", 16)).pack(pady=10)

        # Relógio analógico simplificado
        self.clock = tk.Label(top, font=('Arial', 48), pady=10)
        self.clock.pack()
        self.atualizar_relogio()

        # Calendário
        calendario = tk.Label(top, text=datetime.now().strftime("%B %Y"), font=("Arial", 24))
        calendario.pack()

    def atualizar_relogio(self):
        now = time.strftime("%H:%M:%S")
        self.clock.config(text=now)
        self.clock.after(1000, self.atualizar_relogio)

    def tela_audios_videos(self):
        top = tk.Toplevel(self.master)
        top.title("Áudios e Vídeos")
        tk.Label(top, text="Áudios e Vídeos", font=("Arial", 16)).pack(pady=10)

        tk.Button(top, text="Reproduzir Áudio", command=self.reproduzir_audio).pack(pady=5)
        tk.Button(top, text="Reproduzir Vídeo", command=self.reproduzir_video).pack(pady=5)

    def reproduzir_audio(self):
        # Reproduzir áudio narrativo
        messagebox.showinfo("Áudio", "Reproduzindo áudio...")

    def reproduzir_video(self):
        # Reproduzir vídeo de familiares
        messagebox.showinfo("Vídeo", "Reproduzindo vídeo...")

    def tela_alertas(self):
        top = tk.Toplevel(self.master)
        top.title("Alertas e Notificações")
        tk.Label(top, text="Alertas para Crises", font=("Arial", 16)).pack(pady=10)

        # Simula um alerta
        tk.Button(top, text="Configurar Alerta", command=self.configurar_alerta).pack(pady=5)

    def configurar_alerta(self):
        # Simulação de alerta de crise
        messagebox.showinfo("Alerta", "Configuração de alerta...")

if __name__ == "__main__":
    root = tk.Tk()
    app = AplicativoPordosol(root)
    root.mainloop()
