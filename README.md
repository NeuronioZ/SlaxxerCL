# SlaxxerCL v2.0.0 - Ferramenta de Limpeza de Mensagens Discord

<div align="center">
  ![Versão](https://img.shields.io/badge/versão-2.0.0-blue.svg)
  ![Python](https://img.shields.io/badge/python-3.7+-blue.svg)
  [![Discord](https://img.shields.io/discord/1356478266562711643?color=7289da&label=Discord&logo=discord&logoColor=white)](https://discord.gg/slaxxer)
  </div>

## 📝 Descrição

SlaxxerCL é uma ferramenta de linha de comando (CLI) projetada para ajudar usuários a gerenciar e limpar suas mensagens diretas (DMs) no Discord. Ela permite deletar mensagens em massa, seja todas as mensagens enviadas pelo usuário ou apenas aquelas contendo anexos, com opções para gerenciar múltiplas contas e proteger DMs específicas através de uma whitelist.

**Aviso Importante:** O uso de self-bots (automatizar contas de usuário normais) viola os Termos de Serviço do Discord e pode resultar na **suspensão ou banimento permanente** da sua conta. Use esta ferramenta por sua conta e risco, ciente das possíveis consequências.

## ✨ Funcionalidades Principais

* 🗑️ **Limpeza de Mensagens em DMs:**
    * Deletar **todas** as mensagens enviadas pelo usuário em todas as DMs (exceto as que estão na whitelist).
    * Deletar **apenas** mensagens contendo anexos (imagens, vídeos, arquivos) em todas as DMs (exceto whitelist).
* 🔐 **Gerenciamento de Contas:**
    * Adicionar e salvar tokens de múltiplas contas Discord de forma segura (relativamente, veja avisos).
    * Selecionar facilmente qual conta usar para a limpeza.
    * Remover tokens salvos.
* 🛡️ **Whitelist de Proteção:**
    * Manter uma lista de IDs de usuários cujas DMs **não** devem ser limpas.
    * Adicionar e remover IDs da whitelist através do menu.
* ⚙️ **Controles e Feedback:**
    * **Cooldown Dinâmico:** Ajusta automaticamente o tempo de espera entre as exclusões para evitar rate limits da API do Discord.
    * **Contador de Mensagens:** Mantém um registro local (`counter.json`) do total de mensagens deletadas pela ferramenta.
    * **(Opcional)** Contador Global via Bot: Pode atualizar uma mensagem em um canal específico do Discord com a contagem global (requer configuração de um Bot).
    * **Discord Rich Presence:** Mostra sua atividade atual no Discord (ocioso, limpando DM de X, etc.) e a contagem de mensagens deletadas na sessão/total.
* 🔄 **Atualização Automática:**
    * Verifica automaticamente por novas versões no repositório GitHub (`NeuronioZ/SlaxxerCL`).
    * Oferece a opção de baixar e instalar a atualização automaticamente.

## 🚀 Instalação

1.  **Pré-requisitos:**
    * Python 3.7 ou superior instalado. ([Download Python](https://www.python.org/downloads/))
    * `pip` (gerenciador de pacotes do Python, geralmente incluído na instalação).
    * `git` (opcional, para clonar o repositório).

2.  **Obtenha o Código:**
    * **Opção 1: Git**
        ```bash
        git clone [https://github.com/NeuronioZ/SlaxxerCL.git](https://github.com/NeuronioZ/SlaxxerCL.git)
        cd SlaxxerCL
        ```
    * **Opção 2: Download ZIP**
        * Vá para a página do repositório: [https://github.com/NeuronioZ/SlaxxerCL](https://github.com/NeuronioZ/SlaxxerCL)
        * Clique no botão "Code" e depois em "Download ZIP".
        * Extraia o arquivo ZIP baixado e navegue até a pasta extraída pelo terminal.

3.  **Instale as Dependências:**
    No terminal, dentro da pasta do projeto, execute:
    ```bash
    pip install -r requirements.txt
    ```
    *Nota: O script tentará instalar `pypresence` automaticamente se não for encontrado, mas é recomendado instalar via `requirements.txt`.*

4.  **Execute o Programa:**
    ```bash
    python main.py
    ```
    *Se você compilou um executável (`.exe`), pode executá-lo diretamente.*

## 📋 Requisitos

* Python 3.7+
* Bibliotecas listadas em `requirements.txt`:
    * `requests>=2.31.0`
    * `pypresence>=4.3.0`
    * `urllib3>=2.0.7`

## 🔧 Configuração

* **Token do Discord:** A ferramenta pedirá seu token do Discord na primeira execução ou ao usar a opção "Adicionar/Atualizar Token".
    * **AVISO EXTREMO:** Obter e usar seu token do Discord para automação é **altamente inseguro** e **viola os Termos de Serviço do Discord**. **NUNCA** compartilhe seu token com ninguém. Se seu token for comprometido, sua conta pode ser roubada.
    * Os tokens são salvos no arquivo `tokens.json`. Considere alternativas mais seguras se a segurança for uma preocupação crítica.
* **Whitelist:** IDs de usuários adicionados à whitelist são salvos em `whitelist.json`. Use a opção 6 no menu para gerenciar esta lista.
* **Contador:** A contagem total de mensagens deletadas é salva em `counter.json`.
* **(Avançado/Opcional)** Configurações no `main.py`:
    * Para usar o contador global via Bot, defina `USE_BOT_COUNTER = True` e preencha `BOT_TOKEN`, `COUNTER_CHANNEL_ID`, `COUNTER_MESSAGE_ID`.
    * Para Rich Presence, certifique-se que `USE_RICH_PRESENCE = True` e, se necessário, atualize `CLIENT_ID` e `RPC_IMAGE_KEY`.

## 🎯 Como Usar

1.  Execute o programa (`python main.py` ou o executável).
2.  **Adicione uma conta:** Use a opção `1` para adicionar seu token do Discord.
3.  **Selecione uma conta:** Se tiver múltiplas contas salvas, use a opção `2` para escolher qual usar.
4.  **(Opcional) Gerencie a Whitelist:** Use a opção `6` para adicionar IDs de usuários cujas DMs você **não** quer que sejam limpas.
5.  **Escolha a ação de limpeza:**
    * Opção `4`: Deletar **todas** as suas mensagens nas DMs (exceto whitelist).
    * Opção `5`: Deletar **apenas** mensagens com anexos/imagens nas DMs (exceto whitelist).
6.  **Confirmação:** Você precisará digitar o nome de usuário da conta selecionada para confirmar a ação **irreversível**.
7.  A ferramenta começará a varrer e deletar as mensagens, mostrando o progresso e respeitando os cooldowns.

## ⚠️ Avisos Importantes

* 🚨 **VIOLAÇÃO DOS TERMOS DE SERVIÇO:** Automatizar contas de usuário (self-bots) é contra os Termos de Serviço do Discord. **Sua conta pode ser banida permanentemente.** Use esta ferramenta por sua total conta e risco.
* 🔒 **SEGURANÇA DO TOKEN:** Seu token do Discord é como sua senha. Armazená-lo em `tokens.json` não é idealmente seguro. **Nunca compartilhe este arquivo ou seu token.**
* 🗑️ **AÇÃO IRREVERSÍVEL:** A exclusão de mensagens é **permanente**. Não há como recuperar mensagens deletadas com esta ferramenta. Faça backups se precisar do conteúdo.
* ⏱️ **RATE LIMITS:** A ferramenta tenta gerenciar os rate limits do Discord com cooldowns dinâmicos, mas uma atividade excessiva ainda pode levar a restrições temporárias ou ações pela plataforma.

## 🤝 Contribuindo

Contribuições são bem-vindas! Sinta-se à vontade para:

1.  Fazer um fork do projeto
2.  Criar uma branch para sua feature (`git checkout -b feature/NovaFeature`)
3.  Commit suas mudanças (`git commit -m 'Adiciona NovaFeature'`)
4.  Push para a branch (`git push origin feature/NovaFeature`)
5.  Abrir um Pull Request

## 📄 Licença

Este projeto está licenciado sob a Licença MIT - veja o arquivo `LICENSE` (se existir) para detalhes. *(Nota: Não há arquivo LICENSE no upload inicial, considere adicionar um).*

## 📞 Suporte

* Entre no nosso [servidor Discord](https://discord.gg/slaxxer)
* Abra uma [issue no GitHub](https://github.com/NeuronioZ/SlaxxerCL/issues)

---

<div align="center">
  Desenvolvido com ❤️ para a comunidade Slaxxer. Use com responsabilidade!
</div>
