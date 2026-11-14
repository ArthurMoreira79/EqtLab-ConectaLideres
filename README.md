# Conecta Líderes · EQT Lab

> Plataforma de desenvolvimento para líderes recém-promovidos, criada para o **Desafio 6 do Hackathon Equatorial (EQT Lab)**.

🔗 **Acesse o projeto:** [conecta-lideres-eqtlab.vercel.app](https://conecta-lideres-eqtlab.vercel.app/)

![Next.js](https://img.shields.io/badge/Next.js-16-000000?logo=nextdotjs&logoColor=white)
![React](https://img.shields.io/badge/React-19-61DAFB?logo=react&logoColor=black)
![TypeScript](https://img.shields.io/badge/TypeScript-5-3178C6?logo=typescript&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-4-06B6D4?logo=tailwindcss&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-17-4169E1?logo=postgresql&logoColor=white)
![Drizzle](https://img.shields.io/badge/Drizzle_ORM-C5F74F?logo=drizzle&logoColor=black)
![Gemini](https://img.shields.io/badge/Gemini-8E75B2?logo=googlegemini&logoColor=white)
![Vercel](https://img.shields.io/badge/Deploy-Vercel-000000?logo=vercel&logoColor=white)

## 🎬 Vídeo de apresentação

<p align="center">
  <a href="docs/video/apresentacao.mp4">
    <img src="docs/video/capa.jpg" alt="Vídeo de apresentação do Conecta Líderes" width="720">
  </a>
  <br>
  <sub>Clique na imagem para assistir (1min21s).</sub>
</p>

---

## 📌 Sobre o projeto

Quem acaba de ser promovido a líder costuma aprender "na marra". O **Conecta Líderes** transforma essa transição em uma jornada guiada: a pessoa faz um diagnóstico inicial, recebe uma trilha de desenvolvimento personalizada e pratica liderança no dia a dia com missões avaliadas por IA, acompanhada pela **Clara**, a mentora virtual da plataforma.

### Principais funcionalidades

- **Diagnóstico rápido:** identifica as competências mais fortes e as que precisam de atenção, e ordena a trilha a partir disso.
- **Trilha de módulos:** caminho em pontos, com lições, quizzes e desafios práticos no formato *Aprender → Testar → Aplicar*.
- **Clara, a mentora com IA:** chat integrado ao Gemini, com conversa por voz (reconhecimento e leitura em português) e vídeos de boas-vindas.
- **Missão do dia:** cenários reais de liderança, com resposta aberta e feedback da IA baseado em rubrica.
- **Relatório da IA:** "Seu momento como líder", com forças, pontos de atenção e uma ação para a semana.
- **Painel:** trilha, missão do dia, constância semanal, radar de competências, equipe e comunidade.
- **Comunidade por área:** fórum com perguntas anônimas, melhor resposta e resposta da IA, além dos grupos da equipe.
- **Salas de jogo:** quiz ao vivo no estilo Kahoot, com entrada por código ou QR code, placar e pódio.
- **Perfil gamificado:** avatar editável, XP, níveis, conquistas e histórico de missões.
- Tema claro/escuro com a paleta Equatorial e layout mobile-first.

---

## 📱 Telas

### Painel

<p align="center">
  <img src="docs/telas/painel-inicio.jpg" alt="Painel: boas-vindas e missão do dia" width="200">
  <img src="docs/telas/painel-constancia.jpg" alt="Painel: constância semanal" width="200">
  <img src="docs/telas/painel-radar-equipe.jpg" alt="Painel: radar de competências e equipe" width="200">
  <img src="docs/telas/painel-relatorio-ia.jpg" alt="Painel: relatório gerado por IA" width="200">
</p>

### Trilha

<p align="center">
  <img src="docs/telas/trilha-caminho.jpg" alt="Trilha em pontos com a Clara" width="200">
  <img src="docs/telas/trilha-modulo.jpg" alt="Módulo com etapas Aprender, Testar e Aplicar" width="200">
  <img src="docs/telas/trilha-licao.jpg" alt="Lição em poucos passos" width="200">
  <img src="docs/telas/trilha-quiz.jpg" alt="Quiz do módulo" width="200">
</p>

### Missão do dia e Clara

<p align="center">
  <img src="docs/telas/missao-do-dia.jpg" alt="Missão do dia" width="200">
  <img src="docs/telas/clara-chat.jpg" alt="Chat com a Clara" width="200">
</p>

### Comunidade

<p align="center">
  <img src="docs/telas/comunidade-areas.jpg" alt="Comunidade por área" width="200">
  <img src="docs/telas/comunidade-forum.jpg" alt="Fórum da área" width="200">
</p>

### Perfil

<p align="center">
  <img src="docs/telas/perfil-avatar.jpg" alt="Perfil com avatar" width="200">
  <img src="docs/telas/perfil-estatisticas.jpg" alt="Estatísticas do perfil" width="200">
  <img src="docs/telas/perfil-conquistas.jpg" alt="Conquistas com níveis" width="200">
  <img src="docs/telas/perfil-historico.jpg" alt="Histórico de missões e configurações" width="200">
</p>

---

## 🛠️ Tecnologias

| Camada | Tecnologias |
|---|---|
| Front-end | Next.js 16 (App Router) · React 19 · TypeScript · Tailwind CSS 4 · HeroUI · lucide-react · next-themes |
| Back-end | Route Handlers do Next.js · Zod (validação no cliente e no servidor) · JWT com `jose` |
| Banco de dados | PostgreSQL 17 · Drizzle ORM · Docker Compose |
| IA | Gemini no chat da Clara · camada plugável para avaliações e relatórios (modo simulado ou API compatível com OpenAI) |
| Voz e vídeo | Web Speech API (reconhecimento e síntese de voz) · vídeos da Clara gerados com D-ID |
| Deploy | Vercel |

### Segurança e persistência

- **Contas, sessões, cadastro, diagnóstico, equipes e salas de jogo** ficam no PostgreSQL. XP e progresso das missões ainda ficam no navegador.
- **Sessão** com JWT em cookie `HttpOnly`, validada contra a tabela de sessões, então o logout revoga o acesso de verdade.
- **Senhas** com hash scrypt e sal.
- **Rate limit** no login, no cadastro e na entrada das salas, guardado no banco.
- No chat da Clara, só as mensagens recentes vão para o provedor, e e-mails, CPFs e chaves são mascarados antes do envio.

Os detalhes de rotas, arquitetura, autenticação e salas de jogo estão no [README do app](app/README.md).

---

## 📁 Estrutura

| Pasta | Conteúdo |
|---|---|
| [`app/`](app/) | Aplicação Next.js (front + API). Veja o [README do app](app/README.md). |
| [`docker-compose.yml`](docker-compose.yml) | Banco PostgreSQL local (imagem Bitnami). |
| [`prompt-futuros-lideres.md`](prompt-futuros-lideres.md) | Especificação do produto. |
| [`docs/`](docs/) | Vídeo de apresentação e prints usados neste README. |

---

## 🚀 Como rodar localmente

### 1. Banco de dados (PostgreSQL)

```bash
cp .env.example .env     # opcional: os valores padrão já funcionam
docker compose up -d     # sobe o Postgres e espera ficar saudável
```

Conexão padrão: `postgresql://futuro:futuro_dev@localhost:5434/futuro_lideres` (porta 5434 para não colidir com outros Postgres locais; mude com `POSTGRES_PORT`). Para parar, use `docker compose down`. Os dados ficam no volume; `down -v` apaga tudo.

### 2. Aplicação

```bash
cd app
pnpm install
cp .env.example .env.local   # preencha o JWT_SECRET: openssl rand -base64 48
pnpm db:seed                 # aplica as migrações e cria as contas de teste
pnpm dev
```

Abra http://localhost:3000 e use **Explorar com dados de demonstração** ou **Criar meu perfil** para o fluxo completo de cadastro e diagnóstico. Em desenvolvimento, o seed cria `admin@teste.com` e `jogador@teste.com`, ambos com a senha `Teste1234`.

### Variáveis de ambiente (`app/.env.local`)

| Variável | Obrigatória | Para quê |
|---|---|---|
| `DATABASE_URL` | Sim | Conexão com o PostgreSQL |
| `JWT_SECRET` | Em produção | Assina a sessão (mínimo de 32 caracteres) |
| `GEMINI_API_KEY` | Não | Ativa a IA no chat da Clara. Sem ela, o chat funciona no modo guiado |
| `IA_PROVEDOR` | Não | `simulado` (padrão) ou `compativel-openai`, para avaliações e relatórios |
| `SEED_ADMIN_EMAIL` / `SEED_ADMIN_PASSWORD` | Em produção | Primeiro admin criado pelo `pnpm db:seed` |

O modo demonstração funciona sem banco. Para criar conta e entrar, o banco é necessário.

---

## ☁️ Deploy na Vercel

1. Importe este repositório na Vercel.
2. Em **Root Directory**, escolha `app`.
3. Framework: Next.js (detectado automaticamente).
4. Configure as variáveis `DATABASE_URL` (um PostgreSQL hospedado) e `JWT_SECRET`. `GEMINI_API_KEY` é opcional.
5. Faça o deploy e rode `pnpm db:seed` apontando para o banco de produção, com `SEED_ADMIN_EMAIL` e `SEED_ADMIN_PASSWORD`, para criar o primeiro admin.

---

## 👥 Equipe

Projeto desenvolvido em equipe durante o Hackathon Equatorial (EQT Lab):

| Membro | GitHub |
|---|---|
| Arthur Moreira | [@ArthurMoreira79](https://github.com/ArthurMoreira79) |
| Vinicius | [@nicius2](https://github.com/nicius2) |
| Hellen França | [@hellengfranca](https://github.com/hellengfranca) |
| BGatinho | [@BGatinho](https://github.com/BGatinho) |
| Albert Freitas | |
