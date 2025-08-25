# MidiaReis - Ecossistema de Mídia e E-commerce para Veículos

> Plataforma de anúncios, e-commerce e entretenimento para telas embarcadas em veículos, com arquitetura robusta e foco na operação offline-first.

**Status do Projeto:** Funcional | **Código-Fonte:** Privado

---

### 🎬 Demonstração das Funcionalidades

| Demonstração (GIF) | Funcionalidade |
| :---: | --- |
| [Insira aqui o GIF com a Visão Geral do Player em Ação] | **Visão Geral:** Demonstração do player principal em funcionamento, exibindo diferentes tipos de mídia e o fluxo de interrupção de campanhas. |
| [Insira aqui o GIF do Módulo de Gerenciamento de Campanhas] | **Gerenciamento de Campanhas:** Demonstra o processo de criação, agendamento e edição de campanhas publicitárias através do CMS embarcado. |
| ![Demonstração do Módulo de Pessoas](https://github.com/digaoreisdev/showcase-midiasreis/blob/main/assets/Video-02-Gerenciar-Pessoas.gif?raw=true) | **Gerenciamento de Pessoas/Usuários:** Mostra a interface para administrar os diferentes tipos de usuários do sistema, como motoristas e anunciantes. |
| ![Demonstração do Gerenciar Produtos](https://github.com/digaoreisdev/showcase-midiasreis/blob/main/assets/Video-03-Gerenciar-Produtos.gif?raw=true) | **Gerenciamento de Produtos:** Apresenta o fluxo de cadastro e organização de produtos para o módulo de e-commerce, incluindo preço, estoque e imagens. |
| ![Demonstração do Gerenciar Notícias](https://github.com/digaoreisdev/showcase-midiasreis/blob/main/assets/Video-04-Gerenciar-Not%C3%ADcias.gif?raw=true) | **Gerenciamento de Notícias:** Apresenta o fluxo de importação, edição, exclusão e organização das notícias para o módulo de conforto do player. |
| ![Demonstração do Gerenciar Curiosidades](https://github.com/digaoreisdev/showcase-midiasreis/blob/main/assets/Video%2005%20-%20Gerenciar%20Curiosidades.gif?raw=true) | **Gerenciamento de Curiosidades:** Apresenta o fluxo de importação, edição e organização das curiosidades, permitindo ativar ou inativar cada item da lista de conforto. |
| ![Demonstração do Gerenciar Mídias](https://github.com/digaoreisdev/showcase-midiasreis/blob/main/assets/Video-06-Gerenciar-M%C3%ADdias.gif?raw=true) | **Gerenciamento de Mídias:** Demonstra o fluxo de adicionar, editar e excluir os arquivos de mídia (vídeos/imagens) que serão utilizados nas campanhas. |
| ![Demonstração do Emitir Relatórios](https://github.com/digaoreisdev/showcase-midiasreis/blob/main/assets/Video-08-Relat%C3%B3rios.gif?raw=true) | **Emitir Relatórios:** Demonstração simplificada de uma dos relatórios de exibições de mídias. |

---

### 🎯 Sobre o Projeto

O "MídiasReis" foi concebido para transformar o tempo de viagem de passageiros em uma oportunidade de engajamento e vendas, criando uma nova fonte de receita para motoristas de aplicativo. A plataforma permite que anunciantes gerenciem campanhas de mídia digital (DOOH) e que passageiros acessem entretenimento e comprem produtos diretamente pela tela no encosto do banco, funcionando de forma autônoma mesmo sem conexão constante com a internet.

### ✨ Funcionalidades Principais

* **Player de Mídia Inteligente:** Um motor de exibição que gerencia campanhas publicitárias com metas contratuais, notícias e conteúdo dinâmico.
* **CMS Embarcado 100% Offline:** Um sistema de gerenciamento de conteúdo completo para administração de Campanhas, Mídias, Produtos e Usuários, com persistência de dados local.
* **E-commerce Integrado:** Uma loja virtual para venda de produtos e serviços, com funcionalidades de catálogo e pedido.
* **Integração com APIs Externas:** Enriquecimento da plataforma com dados contextuais e em tempo real (Google Places, FIPE, ViaCEP, Clima, Notícias).
* **Backup e Restauração:** Funcionalidade robusta para portabilidade de dados e mídias através da serialização em JSON e compressão ZIP.
* **Serviços em Background:** Execução de tarefas assíncronas, como a prospecção de leads comerciais baseada na geolocalização do veículo.

### 🧠 Arquitetura e Lógica do Player (Motor V2)

O núcleo do MidiaReis é o seu motor de exibição, projetado para ser um "Gerente de Contrato" que garante o cumprimento das metas de cada campanha.

**Princípio Central:**
O objetivo principal é cumprir as metas de `execucoesPorHora` de cada campanha agendada, utilizando o tempo ocioso para exibir conteúdo de conforto (notícias, curiosidades) e campanhas prioritárias.

**Fluxo de Execução:**

1.  **Fase 1: Execução Inicial Obrigatória**
    * Ao iniciar, o sistema executa uma vez cada campanha agendada (normal) para calcular e salvar seu `proximaExecucaoTimestamp`, inserindo-a oficialmente na fila de prioridade.

2.  **Fase 2: Loop Principal de Exibição**
    * **Verificação de Interrupção:** O sistema sempre verifica se uma campanha agendada alcançou seu `proximaExecucaoTimestamp`. Em caso positivo, ela interrompe qualquer fluxo, é exibida, e reagendada.
    * **Ciclo de Conforto:** Se nenhuma campanha agendada estiver pronta, o sistema exibe um item do ciclo de conforto (`Loja -> Notícia -> Curiosidade -> Campanhas Prioritárias`).

**Controle de Estabilidade:**
O fluxo é controlado por um mecanismo de trava (`isLoopBusy`) que previne chamadas concorrentes, eliminando bugs de sobreposição de áudio/vídeo e garantindo uma execução estável e previsível.

### 🛠️ Tecnologias Utilizadas

* **Plataforma:** Android Nativo
* **Linguagem:** Kotlin
* **Banco de Dados:** RoomDB (Persistência Offline)
* **Comunicação com API:** Retrofit2
* **Serialização:** Gson
* **Arquitetura:** MVVM, Coroutines, LiveData

### 👨‍💻 Meu Papel no Projeto

Atuei como o único desenvolvedor do MidiaReis, responsável pelo ciclo completo do projeto: da concepção e arquitetura da solução à implementação de todas as funcionalidades do aplicativo Android, incluindo o motor do player e o CMS embarcado.

### 📫 Contato

* **LinkedIn:** [Insira aqui o link para o seu perfil no LinkedIn]
* **E-mail:** [Insira aqui o seu e-mail de contato]
