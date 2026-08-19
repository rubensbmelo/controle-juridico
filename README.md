# Controle Juridico

Dashboard pessoal para acompanhamento de processos, valores, riscos e movimentacoes.

## Estado atual

O `index.html` preserva a interface original e, por enquanto, salva os dados no `localStorage` do navegador. Isso evita a perda imediata de dados, mas ainda nao sincroniza dispositivos.

## Arquitetura final

- Interface: HTML/CSS/JavaScript existente.
- Persistencia: Supabase (PostgreSQL).
- Login: Supabase Auth com login interno e senha.
- Publicacao: GitHub Pages, Vercel ou Netlify.

O frontend ja esta configurado para usar o Supabase quando houver uma sessao autenticada. A tela mostra apenas o login `sergiofilho`; internamente ele usa um e-mail tecnico para o Supabase.

Ao entrar pela primeira vez, os dados iniciais do HTML sao enviados para o banco se a tabela ainda estiver vazia.

## Configuracao inicial

1. Crie um projeto no Supabase.
2. Execute `supabase-schema.sql` no SQL Editor.
3. Ative o provedor de e-mail em Authentication.
4. Nunca coloque a chave `service_role` no HTML. O frontend usa somente a chave publica `anon`, com RLS habilitado.

## Migracao dos dados

Os dados do bloco `SEED` do HTML podem ser importados uma vez para a tabela `processes`. Eventos existentes devem ser importados para `events`.

Antes da publicacao, revise e anonimize os dados reais usados em demonstracoes. O repositorio nao deve conter credenciais, tokens ou exportacoes de processos.
