# Controle Juridico

Dashboard pessoal para acompanhamento de processos, valores, riscos e movimentacoes.

## Estado atual

O `index.html` usa o Supabase como fonte principal e mantem uma copia local para consulta quando a conexao esta indisponivel. Os dados reais nao ficam embutidos no codigo.

## Arquitetura final

- Interface: HTML/CSS/JavaScript existente.
- Persistencia: Supabase (PostgreSQL).
- Login: Supabase Auth com login interno e senha.
- Publicacao: GitHub Pages.

O frontend usa o Supabase somente depois da autenticacao. A tela mostra apenas o login `sergiofilho`; internamente ele usa um e-mail tecnico para o Supabase.

O painel inclui busca, filtros, movimentacoes, prazos e alertas, backup JSON e layout responsivo.

Processos, eventos e prazos sao sincronizados com regras RLS por usuario.

A exclusao de processos exige conexao com o Supabase. Se o sistema estiver offline, a operacao e recusada para evitar que um processo apagado localmente reapareca depois.

## Configuracao inicial

1. Crie um projeto no Supabase.
2. Execute `supabase-schema.sql` no SQL Editor.
3. Crie o usuario interno em Authentication e desative novos cadastros.
4. Nunca coloque a chave `service_role` no HTML. O frontend usa somente a chave publica `anon`, com RLS habilitado.

## Backup

Use o botao `backup` depois de entrar. O arquivo JSON exportado deve ser guardado fora do repositorio e em local seguro.

O repositorio nao deve conter credenciais secretas, backups ou exportacoes de processos. A chave publishable pode aparecer no frontend, desde que o RLS permaneça habilitado.
