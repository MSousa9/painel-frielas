# Painel de Jogos SC Frielas

Painel para o ecrã do clube. Mostra os jogos de todos os escalões, a classificação e os resultados, e atualiza-se sozinho duas vezes por semana a partir do portal oficial da FPF (resultados.fpf.pt, AF Lisboa).

## O que está neste pacote

| Ficheiro | Para que serve |
|---|---|
| `index.html` | O painel (é isto que abres no ecrã) |
| `data.json` | Jogos e classificações (preenchido automaticamente) |
| `scripts/atualizar.py` | Programa que lê o portal da FPF |
| `.github/workflows/atualizar.yml` | Agenda: quinta-feira às 12:00 e domingo às 21:00 (hora UTC) |

## Como pôr a funcionar (cerca de 10 minutos, só uma vez)

**1. Conta.** Cria uma conta grátis em github.com.

**2. Repositório.** Carrega em **+ → New repository**. Dá-lhe um nome (por exemplo `painel-frielas`), escolhe **Public** e cria.

**3. Ficheiros.** No repositório, carrega em **Add file → Upload files** e arrasta para lá `index.html`, `data.json`, `README.md` e a pasta `scripts`. Confirma com **Commit changes**.

**4. Agenda automática.** A pasta `.github` é escondida em alguns computadores, por isso cria-a à mão:
- **Add file → Create new file**
- No nome escreve exatamente: `.github/workflows/atualizar.yml` (ao escrever as barras, o GitHub cria as pastas)
- Cola lá o conteúdo do ficheiro `atualizar.yml` deste pacote e confirma com **Commit changes**.

**5. Permissões.** Em **Settings → Actions → General → Workflow permissions** escolhe **Read and write permissions** e grava.

**6. Publicar o painel.** Em **Settings → Pages**, em *Source* escolhe **Deploy from a branch**, ramo **main**, pasta **/ (root)** e grava. Ao fim de um ou dois minutos o endereço aparece ali: `https://O-TEU-UTILIZADOR.github.io/painel-frielas/`

**7. Primeira leitura.** Vai a **Actions → Atualizar jogos e classificações → Run workflow**. Demora uns minutos. Quando ficar verde, abre o endereço do painel: já vem com os jogos e as classificações oficiais.

## No ecrã do clube

Abre o endereço no navegador e põe em ecrã inteiro (F11). O painel volta a ler os dados sozinho de 30 em 30 minutos.

Os **patrocinadores** adicionam-se no ⚙ (canto inferior direito) **no próprio navegador do ecrã**: as imagens ficam guardadas nesse navegador. Se mudares de computador ou limpares os dados do navegador, voltas a adicioná-las.

## Se alguma coisa correr mal

- **Actions fica vermelho:** abre a execução que falhou, desce até *Artifacts* e descarrega `diagnostico`. Envia-me esse ficheiro e a mensagem de erro que aparece, e eu corrijo o programa.
- **Um escalão não aparece com classificação:** alguns escalões mais novos (por exemplo Sub-10) não têm classificação publicada no portal. Esses continuam a mostrar o calendário que já vinha no painel.
- **O nome do clube no portal mudou:** abre `scripts/atualizar.py` e ajusta a linha `CLUBE_RE`.
- **Nova época:** em `scripts/atualizar.py` mudam-se `SEASON_ID`, `SEASON_START` e os números das competições (estão no portal, na lista de competições da AF Lisboa).
- **Se o agendamento parar** (o GitHub pausa agendas de repositórios sem atividade durante muito tempo): em **Actions**, carrega no botão para o voltar a ativar.

## Nota

O programa lê o portal da FPF apenas duas vezes por semana, com pausas entre pedidos, para uso do clube. Não li os termos de utilização do portal, por isso convém dares-lhes uma vista de olhos.
