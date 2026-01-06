# Projeto PVR - ClashBound

## 📝 Descrição do Projeto
Este projeto foi desenvolvido para a unidade curricular de **Programação de Videojogos em Rede (PVR)**. O objetivo principal é a criação de um jogo multijogador utilizando o motor de jogo **Unity** e a biblioteca **Photon Unity Networking (PUN 2)**.

O foco do trabalho reside na implementação de arquiteturas cliente-servidor, sincronização de estados em tempo real e gestão de comunicação via rede.

---

## 🛠️ Implementação Técnica e Protocolos

### 1. Protocolos de Comunicação (TCP & UDP)
O projeto utiliza uma abordagem híbrida gerida pelo motor do Photon:
* **UDP (User Datagram Protocol):** Utilizado para o tráfego de alta performance, como a sincronização de posições (`Transform`) e rotações dos jogadores, onde a baixa latência é crítica.
* **TCP (Transmission Control Protocol):** Utilizado para operações de controlo que exigem fiabilidade total, como o login nos servidores, entrada em salas (Lobby) e eventos de carregamento de cena.

### 2. Netcode & Photon for Unity
Para cumprir os requisitos da disciplina, implementámos:
* **PhotonView:** Componente essencial para identificar e gerir a autoridade de cada objeto na rede.
* **Sincronização de Estado:** Uso de `OnPhotonSerializeView` para envio contínuo de dados e `PhotonTransformView` para interpolação suave.
* **RPCs (Remote Procedure Calls):** Utilizados para disparar eventos pontuais que todos os clientes devem executar simultaneamente (ex: início da partida, efeitos sonoros ou morte).
* **Lobby System:** Interface para criação e junção de salas de forma dinâmica.

---

## 🎮 Mecânicas de Rede
* **Instanciação em Rede:** Jogadores são criados dinamicamente via `PhotonNetwork.Instantiate`.
* **Verificação de Autoridade:** Verificação rigorosa de `photonView.IsMine` para garantir que um jogador apenas controla o seu próprio personagem.
* **Sincronização de Animações:** Implementação de `PhotonAnimatorView` para replicar o estado visual de todos os clientes.

---

## 📁 Estrutura do Projeto (Fases 1 e 2)
* **Fase 1:** Planeamento, definição do título, descrição das mecânicas base e configuração inicial do ambiente de rede.
* **Fase 2:** Implementação final, polimento das mecânicas multiplayer, tratamento de exceções (ex: perda de conexão) e conclusão do relatório.
