<div align="center">

# 🌐 erickystn.github.io — Portal & Redirecionamento Canônico

**Ponto de entrada canônico e hub de resolução de domínio pessoal no GitHub Pages**

[![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-Ativo-brightgreen?style=for-the-badge&logo=github&logoColor=white)](https://erickystn.github.io/)
[![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)](https://developer.mozilla.org/pt-BR/docs/Web/HTML)
[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript)
[![Google Search Console](https://img.shields.io/badge/Google%20Search%20Console-Verificado-4285F4?style=for-the-badge&logo=google&logoColor=white)](https://search.google.com/search-console)
[![Licença](https://img.shields.io/badge/Licen%C3%A7a-MIT-blue?style=for-the-badge)](./LICENSE)

</div>

---

## 🔗 Link de Deploy & Acesso ao Vivo

- **Domínio Raiz (Host):** [https://erickystn.github.io](https://erickystn.github.io)
- **Destino Canônico do Portfólio:** [https://erickystn.github.io/portfolio_generation/](https://erickystn.github.io/portfolio_generation/)

---

## 📖 Visão Geral

O repositório **`erickystn.github.io`** desempenha a função estratégica de hospedar o site de nível superior (User Site) do GitHub Pages do desenvolvedor [Ericky Santana (@erickystn)](https://github.com/erickystn).

Atuando como um *hub de roteamento e redirecionamento canônico*, o projeto centraliza o acesso ao domínio base e encaminha visitantes de forma transparente para a aplicação principal de portfólio interativo ([`portfolio_generation`](https://github.com/erickystn/portfolio_generation)). Além disso, o repositório mantém os tokens de autenticação criptográfica para verificação de propriedade e indexação de domínio no Google Search Console.

---

## ✨ Funcionalidades

- **Roteamento Canônico com Zero Latência:** Redirecionamento instantâneo via cabeçalho HTML `<meta http-equiv="refresh">` (tempo de espera `0s`).
- **Navegação Resiliente (Histórico Limpo):** Uso de `window.location.replace()` em JavaScript para substituir o registro de histórico de navegação, evitando loops no botão "Voltar" do navegador.
- **Fallback de Acessibilidade:** Mensagem estática e link manual para usuários ou agentes de indexação (crawlers) com execução de scripts desabilitada.
- **Validação de Propriedade Web:** Arquivo de autenticação estático para indexação, métricas de rastreamento e auditoria de SEO através do Google Search Console.

---

## 🎯 Diferenciais e Destaques Técnicos

1. **Estratégia de Redirecionamento Híbrida (Defense in Depth):** Combinação de diretiva declarativa de meta refresh no `<head>` com execução programática de substituição de URL no DOM.
2. **Preservação da Experiência do Usuário (No Navigation Trap):** Ao invés de `window.location.href`, o emprego estrito de `window.location.replace()` garante que a página de trânsito não polua o *Session History*, permitindo que o usuário retorne à origem com um único clique no botão Voltar.
3. **Padrão de Hub Desacoplado:** Permite alterar o destino de produção do portfólio ou adicionar landing pages institucionais no futuro sem necessidade de alterar o apontamento de DNS ou URLs públicas compartilhadas em currículos e redes profissionais.

---

## 🏗️ Arquitetura e Estrutura de Arquivos

A organização do repositório é minimalista e voltada à entrega estática imediata via CDN do GitHub:

```text
erickystn.github.io/
├── index.html                   # Ponto de entrada com script de redirecionamento canônico
├── google842991cb476e922c.html   # Token de verificação de propriedade do Google Search Console
└── README.md                    # Documentação técnica completa do repositório
```

---

## 🎨 UX e Fluxo de Resolução de Domínio

O diagrama textual abaixo ilustra o fluxo de requisição e resolução quando o usuário acessa o domínio raiz:

```text
[Usuário / Recrutador]
         │
         ▼
[Acesso: https://erickystn.github.io]
         │
         ├──────────────────────────────────────────────┐
         │                                              │
         ▼                                              ▼
[Execução JS: window.location.replace()]     [Fallback Meta-Refresh: 0s]
         │                                              │
         └──────────────────────┬───────────────────────┘
                                │
                                ▼
         [Substituição limpa no histórico do browser]
                                │
                                ▼
         [Exibição: https://erickystn.github.io/portfolio_generation/]
```

---

## 🧭 Passo a Passo de Uso para o Visitante

1. Acesse o endereço [https://erickystn.github.io](https://erickystn.github.io) no seu navegador.
2. A aplicação detectará automaticamente o carregamento e realizará a transição transparente para o portfólio interativo.
3. Caso o seu navegador utilize bloqueador de scripts ou modo estrito, um link direto (*"clique aqui"*) permanecerá visível para navegação manual.

---

## ⚙️ Requisitos e Hospedagem

O projeto requer apenas um servidor web estático ou a ativação nativa do GitHub Pages:

- **Hospedagem:** GitHub Pages
- **Branch Fonte:** `main`
- **Diretório:** `/ (root)`
- **HTTPS:** Ativado por padrão com certificado TLS gerenciado pelo GitHub

---

## 🚀 Como Executar Localmente

Para testar o comportamento do redirecionamento e a integridade da página em ambiente de desenvolvimento:

### Opção 1: Via Python (Recomendado)
```bash
# Clone o repositório
git clone https://github.com/erickystn/erickystn.github.io.git

# Acesse o diretório
cd erickystn.github.io

# Inicie o servidor estático na porta 8000
python3 -m http.server 8000
```
Acesse `http://localhost:8000` no navegador.

### Opção 2: Via Node.js (`npx serve`)
```bash
npx serve .
```

### Opção 3: Extensão Live Server (VS Code)
Abra a pasta do projeto no VS Code, clique com o botão direito no `index.html` e selecione **"Open with Live Server"**.

---

## 💻 Exemplos de Código

Abaixo está o trecho em destaque implementado no `index.html`, demonstrando a estratégia de substituição do histórico:

```html
<meta http-equiv="refresh" content="0; url=https://erickystn.github.io/portfolio_generation/">
<script>
    // O replace() não salva essa página no histórico de navegação, 
    // permitindo que o usuário consiga usar o botão "voltar" normalmente.
    window.location.replace("https://erickystn.github.io/portfolio_generation/");
</script>
```

---

## 🛠️ Tecnologias Utilizadas

| Tecnologia | Finalidade |
| :--- | :--- |
| **HTML5** | Estruturação semântica, meta tags de controle e link de fallback acessível. |
| **JavaScript (ES5/ES6)** | Roteamento dinâmico e gestão de histórico via `window.location.replace`. |
| **GitHub Pages** | Infraestrutura de hospedagem estática global com entrega de borda (CDN). |
| **Google Search Console** | Rastreamento, auditoria de indexação e validação de propriedade do domínio. |

---

## 📈 Melhorias e Próximos Passos (Roadmap)

- [ ] Implementação de página *splash* institucional completa caso o portfólio seja migrado para domínio customizado.
- [ ] Adição de tags Open Graph (`og:image`, `og:title`, `og:description`) para previews em redes sociais (WhatsApp, LinkedIn, Twitter/X).
- [ ] Inclusão de `robots.txt` e `sitemap.xml` para otimização de SEO e controle de indexação.

---

## 🤝 Como Contribuir

Contribuições para melhorias no roteamento ou nas diretivas de SEO são sempre bem-vindas:

1. Faça um **Fork** do repositório.
2. Crie uma branch para sua modificação: `git checkout -b feature/minha-melhoria`.
3. Faça o commit das suas alterações: `git commit -m "feat: otimiza diretivas de meta tags"`.
4. Envie para o seu repositório: `git push origin feature/minha-melhoria`.
5. Abra um **Pull Request**.

---

## 👤 Autor & 📄 Licença

Desenvolvido por **[Ericky Santana](https://github.com/erickystn)**.

Este projeto está sob a licença **MIT** — consulte o arquivo [LICENSE](./LICENSE) para mais detalhes.