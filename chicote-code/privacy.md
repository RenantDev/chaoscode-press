# Política de Privacidade — Chicote Code

**Última atualização:** 14 de maio de 2026
**Aplicação:** Chicote Code (Microsoft Store: ChicoteCode.ChicoteCode)
**Responsável:** RENANT BERNABE DESENVOLVIMENTO DE SOFTWARE LTDA (CNPJ 57.651.869/0001-13)
**Contato:** contato@chaoscode.ai

> Esta política descreve quais dados o **Chicote Code** acessa, onde armazena e com quem compartilha. O texto desta página é a fonte canônica e é publicado também em https://chaoscode.ai/chicote-code/privacy.

---

## 1. Resumo executivo

- **Não coletamos telemetria.** O Chicote Code não envia dados de uso para servidores nossos.
- **Tudo fica local.** Configurações ficam em `%APPDATA%\chicote-code\` no seu computador.
- **Tokens da Twitch ficam protegidos.** Armazenados no **Windows Credential Manager** (criptografado pelo sistema operacional), nunca em arquivo texto.
- **Você controla tudo.** Pode revogar acesso, desconectar a Twitch e apagar os dados a qualquer momento.

---

## 2. Quais dados o aplicativo acessa

### 2.1 Dados da Twitch (somente quando você conecta)

Ao conectar sua conta da Twitch no painel, o aplicativo solicita autorização para o escopo **`channel:read:redemptions`**, que permite:

- Ler o nome do seu canal
- Receber notificações em tempo real quando viewers resgatam pontos do canal (Channel Points)
- Listar as recompensas (rewards) configuradas no seu canal

**O que recebemos em cada redemption:** nome de exibição (display name) do viewer, ID da recompensa, timestamp e mensagem opcional. Esses dados ficam **apenas em memória** durante a execução para disparar a animação correspondente.

### 2.2 Tokens OAuth

Os tokens de acesso e atualização emitidos pela Twitch são armazenados no **Windows Credential Manager** via API nativa do Windows. Eles **nunca** são gravados em arquivo de configuração nem enviados para servidores externos.

### 2.3 Configuração local

As preferências do aplicativo (animações, bindings de recompensas, monitor selecionado, porta do servidor local, etc.) são gravadas em `%APPDATA%\chicote-code\config.json`. Esse arquivo permanece exclusivamente no seu computador.

### 2.4 Hooks do Claude Code (opcional)

Se você habilitar a integração com o Claude Code, o aplicativo lê e modifica `%USERPROFILE%\.claude\settings.json` **somente quando você clica explicitamente** em "Instalar hooks" no painel. A modificação é reversível com um clique em "Desinstalar hooks".

---

## 3. Servidor HTTP local

O Chicote Code expõe um servidor HTTP em **`127.0.0.1:8731`** (loopback) por padrão, usado para receber gatilhos do Claude Code e servir a página do OBS Browser Source.

- Por padrão, o servidor escuta apenas em **loopback** (somente o seu computador acessa).
- Existe um toggle no painel chamado **"Expor para a rede"** que, se ativado, permite acesso de outros dispositivos na sua rede local. **Esse toggle vem desativado.**
- O servidor **não** aceita conexões da internet pública.

---

## 4. Compartilhamento de dados

**Não compartilhamos seus dados com terceiros.** O Chicote Code não envia informações para nenhum servidor controlado por nós.

A única comunicação externa do aplicativo é diretamente com a **API da Twitch** (`id.twitch.tv`, `api.twitch.tv`, `eventsub.wss.twitch.tv`), regida pela [Política de Privacidade da Twitch](https://www.twitch.tv/p/legal/privacy-notice/).

---

## 5. Onde os dados ficam

| Dado | Localização |
|---|---|
| Configuração geral | `%APPDATA%\chicote-code\config.json` |
| Sprites customizados | `%APPDATA%\chicote-code\sprites\` |
| Tokens OAuth Twitch | Windows Credential Manager (chave: `chicote-code:twitch`) |
| Hooks do Claude Code | `%USERPROFILE%\.claude\settings.json` (apenas seções `hooks` adicionadas pelo app) |

Nenhum desses dados sai do seu computador.

---

## 6. Como remover seus dados

Para apagar **todos** os dados criados pelo Chicote Code:

1. **Desinstalar o aplicativo** pela Microsoft Store (Configurações → Aplicativos → Chicote Code → Desinstalar)
2. **Apagar a pasta de configuração:** `%APPDATA%\chicote-code\`
3. **Remover tokens OAuth:** abrir o "Gerenciador de Credenciais" do Windows → "Credenciais Genéricas" → procurar entradas com prefixo `chicote-code:` e excluir
4. **Reverter hooks do Claude Code:** se ainda estiverem ativos, basta desinstalar pelo painel antes da etapa 1, ou remover manualmente as entradas em `%USERPROFILE%\.claude\settings.json`

Você também pode revogar o acesso da Twitch a qualquer momento em https://www.twitch.tv/settings/connections (procure por "Chicote Code" na lista de conexões).

---

## 7. Crianças

O Chicote Code não é direcionado a crianças menores de 13 anos. Não coletamos intencionalmente dados de menores. A classificação etária na Microsoft Store é **3+/Everyone**.

---

## 8. Alterações nesta política

Mudanças significativas serão refletidas nesta página com atualização da data no topo. Versões anteriores ficam preservadas no histórico Git público do projeto.

---

## 9. Contato

Dúvidas, solicitações de remoção ou relatos de incidentes:

**E-mail:** contato@chaoscode.ai
**Razão social:** RENANT BERNABE DESENVOLVIMENTO DE SOFTWARE LTDA
**CNPJ:** 57.651.869/0001-13
**Endereço:** Av. Paulista, 1106, sala 01, 16º andar, São Paulo - SP, CEP 01310-914, Brasil
