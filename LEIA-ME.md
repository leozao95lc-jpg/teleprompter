# Teleprompter Pro — como publicar e instalar

App web instalável (PWA) para iPhone. Sem login, sem servidor próprio, sem custo. Roteiros e vídeos ficam no aparelho.

## Arquivos

| Arquivo | Função |
|---|---|
| `index.html` | O app inteiro (interface, editor, teleprompter, câmera) |
| `sw.js` | Service worker: faz o app abrir sem internet |
| `manifest.webmanifest` | Nome, ícone e modo tela cheia do app instalado |
| `icons/` | Ícones da Tela de Início |

## 1. Publicar de graça (uma vez, pelo computador)

O iPhone só libera câmera e microfone para páginas em **HTTPS**. Abrir o `index.html` direto do app Arquivos não funciona para gravar.

### Opção recomendada: GitHub Pages

1. Crie uma conta gratuita em github.com.
2. Clique em **New repository**, dê o nome `teleprompter`, deixe **Public** e crie.
3. Clique em **Add file › Upload files** e arraste **o conteúdo** desta pasta (index.html, sw.js, manifest.webmanifest e a pasta icons). Clique em **Commit changes**.
4. Vá em **Settings › Pages**. Em *Build and deployment*, escolha **Deploy from a branch**, branch **main**, pasta **/ (root)** e salve.
5. Em 1 a 2 minutos o app fica em `https://SEU-USUARIO.github.io/teleprompter/`.

O repositório público expõe só o código do app. Seus roteiros e vídeos nunca vão para lá: ficam no iPhone.

### Alternativas

- **Netlify Drop** (app.netlify.com/drop): arraste a pasta. Crie a conta gratuita para o site não expirar.
- **Cloudflare Pages**: plano gratuito, upload direto da pasta.

## 2. Instalar no iPhone

1. Abra o endereço no **Safari** (não no Chrome nem no navegador do Instagram/WhatsApp).
2. Toque em **Compartilhar**. Em versões recentes do iOS ele pode estar no menu **•••**.
3. Toque em **Adicionar à Tela de Início** e confirme.
4. Abra sempre pelo ícone. Na primeira abertura com internet, o app fica salvo para uso offline.
5. Abra **Ajuda › Diagnóstico deste aparelho** para ver o que o seu iOS libera de verdade.

## 3. O que funciona instalado

- Editor, biblioteca, salvamento automático, importar/exportar TXT.
- Teleprompter com velocidade em palavras por minuto, fonte, entrelinha, largura, alinhamento, espelhamento, contagem regressiva e linha-guia.
- Câmera frontal/traseira com texto na faixa superior e gravação de vídeo com áudio (iOS 14.3 ou superior), sem o texto no arquivo.
- Revisão da tomada e salvamento no app Fotos pelo menu Compartilhar (**Salvar Vídeo**).
- Abre sem barras do Safari e funciona offline.

## 4. Limites que continuam por causa do iOS

- Uma página web **não consegue flutuar sobre o app Câmera**. Para qualidade máxima (4K, estabilização, Modo Cinema, troca de lente), grave com a Câmera nativa e leia o roteiro em outro aparelho (Modo C, explicado dentro do app).
- Trocar de app ou bloquear a tela corta câmera e microfone. O app encerra a gravação e tenta preservar o trecho.
- A tomada fica na memória até ser salva. Tomadas muito longas podem fazer o Safari recarregar a página. Salve cada tomada.
- O app instalado e o Safari guardam dados separados. Use **Exportar TXT** como backup.
- Isto não é um app da App Store: não tem acesso às APIs nativas de câmera (foco manual, lentes, ProRes).

## 5. Atualizar o app depois

Substitua os arquivos no repositório e altere a linha `const VERSION = 'tp-v1.0.0'` em `sw.js` (por exemplo para `tp-v1.0.1`). O iPhone baixa a nova versão em segundo plano e aplica na abertura seguinte. Os roteiros salvos não são apagados.
