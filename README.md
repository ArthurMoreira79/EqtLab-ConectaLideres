# Conecta Líderes · EQT Lab

> Plataforma de desenvolvimento para líderes recém-promovidos, criada para o **Desafio 6 do Hackathon Equatorial (EQT Lab)**.

🔗 **Acesse o projeto:** [conecta-lideres-eqtlab.vercel.app](https://conecta-lideres-eqtlab.vercel.app/)

![Next.js](https://img.shields.io/badge/Next.js-16-000000?logo=nextdotjs&logoColor=white)
![React](https://img.shields.io/badge/React-19-61DAFB?logo=react&logoColor=black)
![TypeScript](https://img.shields.io/badge/TypeScript-5-3178C6?logo=typescript&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-4-06B6D4?logo=tailwindcss&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?logo=postgresql&logoColor=white)
![Vercel](https://img.shields.io/badge/Deploy-Vercel-000000?logo=vercel&logoColor=white)

---

## 📌 Sobre o projeto

Quem acaba de ser promovido a líder costuma aprender "na marra". O **Conecta Líderes** transforma essa transição em uma jornada guiada: a pessoa faz um diagnóstico inicial, recebe uma trilha de desenvolvimento personalizada e pratica liderança no dia a dia com missões avaliadas por IA.

### Principais funcionalidades

- **Diagnóstico rápido** — identifica as competências mais fortes e as que precisam de atenção, e ordena a trilha a partir disso.
- **Trilha de módulos** — caminho em pontos com lições, quizzes e desafios práticos, acompanhado pela assistente Clara.
- **Missão do dia** — cenários reais de liderança, com escolha + justificativa e feedback da IA baseado em rubrica.
- **Relatório da IA** — "Seu momento como líder", com a evolução das competências.
- **Painel (dashboard)** — trilha, missão do dia, constância semanal, radar de competências, equipe e comunidade.
- **Comunidade** — fórum anônimo por área, com marcação de resposta útil, melhor resposta e resposta da IA.
- **Salas de jogo** — o admin cria uma sala com perguntas e as pessoas entram por código ou QR code.
- **Perfil gamificado** — avatar editável, XP, conquistas com níveis e histórico.
- Tema claro/escuro com a paleta Equatorial e layout mobile-first.

---

## 🛠️ Tecnologias

| Camada | Tecnologias |
|---|---|
| Front-end | Next.js 16 (App Router) · React 19 · TypeScript · Tailwind CSS 4 · HeroUI · lucide-react · next-themes |
| Back-end | Route Handlers do Next.js · Zod (validação) · JWT com `jose` |
| Banco de dados | PostgreSQL · Drizzle ORM · Docker Compose |
| IA | Camada plugável: modo simulado ou qualquer API compatível com OpenAI |
| Deploy | Vercel |

---

## 📁 Estrutura

| Pasta | Conteúdo |
|---|---|
| [`app/`](app/) | Aplicação Next.js (front + API). Veja o [README do app](app/README.md) para telas, rotas da API, arquitetura e autenticação. |
| [`docker-compose.yml`](docker-compose.yml) | Banco PostgreSQL local (imagem Bitnami). |
| [`prompt-futuros-lideres.md`](prompt-futuros-lideres.md) | Especificação do produto. |

---

## 🚀 Como rodar localmente

### Banco de dados (PostgreSQL)

```bash
cp .env.example .env     # opcional: os valores padrão já funcionam
docker compose up -d     # sobe o Postgres e espera ficar saudável
docker compose down      # para (os dados ficam no volume); use `down -v` para apagar tudo
```

Conexão padrão: `postgresql://futuro:futuro_dev@localhost:5434/futuro_lideres` (porta 5434 para não colidir com outros Postgres locais; mude com `POSTGRES_PORT`).

> A imagem é `bitnamilegacy/postgresql`: a Bitnami moveu as tags versionadas para esse namespace e o `bitnami/postgresql` só mantém a tag `latest`. O app ainda não lê o banco — hoje o estado fica no navegador (veja “Para a equipe de back-end” no README do app).

### Aplicação

```bash
cd app
pnpm install
cp .env.example .env.local   # preencha o JWT_SECRET: openssl rand -base64 48
pnpm dev
```

Abra http://localhost:3000 e use **Explorar com dados de demonstração** ou **Criar meu perfil** para o fluxo completo de cadastro → diagnóstico.

---

## ☁️ Deploy na Vercel

1. Importe este repositório na Vercel.
2. Em **Root Directory**, escolha `app`.
3. Framework: Next.js (detectado automaticamente). Não é preciso variável de ambiente: sem `IA_PROVEDOR`, a avaliação usa o modo simulado.
4. Deploy.

---

## 👥 Equipe

Projeto desenvolvido em equipe durante o Hackathon Equatorial (EQT Lab).

