# Tutorial Rápido e Prático: Usando a Raspberry Pi Zero W no Modo Wi-Fi

## Introdução

Este tutorial tem como objetivo guiar os usuários na configuração da **Raspberry Pi Zero W** para funcionar no modo Wi-Fi, sem a necessidade de monitor ou periféricos (headless). Veremos desde a instalação da imagem do sistema operacional até o acesso remoto via **SSH**, permitindo que você utilize a Raspberry Pi em projetos IoT, automação ou servidores pequenos.

Durante o processo de configuração, enfrentamos alguns desafios relacionados à conectividade Wi-Fi com imagens mais recentes do sistema operacional. A solução encontrada foi utilizar uma versão específica do sistema operacional que se mostrou estável e funcional na Raspberry Pi Zero W.

---

## Por que a Imagem "Raspberry Pi OS (Legacy, 32-bit)"?

### Problema com Imagens Mais Recentes

Ao tentar configurar a Raspberry Pi Zero W usando versões mais recentes do Raspberry Pi OS (baseadas em 64 bits ou versões mais modernas), muitos usuários, inclusive nós, encontramos problemas ao tentar conectar a Raspberry Pi ao Wi-Fi. Esses problemas envolvem:

- Falhas de conectividade com redes Wi-Fi.
- O dispositivo não é detectado na rede após inicialização.
- Dificuldade em acessar via SSH usando `raspberrypi.local`.

### A Solução: Raspberry Pi OS (Legacy, 32-bit)

A versão **Raspberry Pi OS (Legacy, 32-bit)**, que é uma versão mais antiga e estável, mostrou-se mais compatível com o hardware da **Raspberry Pi Zero W**. Esse sistema é baseado em uma versão anterior do Debian, chamada Buster, e mantém suporte para dispositivos de hardware mais antigos como a Raspberry Pi Zero W, além de ser mais leve e adequado para recursos limitados.

Essa versão foi a única que, durante nossos testes, permitiu que a Raspberry Pi Zero W se conectasse automaticamente ao Wi-Fi e fosse acessível via SSH sem problemas. Recomendamos essa versão para quem está encontrando dificuldades com as versões mais recentes.

---

## Pré-requisitos

- Uma **Raspberry Pi Zero W**.
- Um **cartão microSD** de pelo menos **4 GB**.
- Um computador com um leitor de cartão SD.
- **Acesso a uma rede Wi-Fi**.
- **Bitvise SSH Client** (ou outro cliente SSH de sua escolha) para acessar a Raspberry Pi remotamente.

---

## Passo a Passo

### 1. Baixar e Gravar a Imagem do Sistema Operacional

1. Acesse o [site oficial da Raspberry Pi](https://www.raspberrypi.org/software/operating-systems/) e role para baixo até encontrar a versão **Raspberry Pi OS (Legacy, 32-bit)**.
2. Baixe a imagem do sistema operacional.
3. Use uma ferramenta como o **Raspberry Pi Imager** ou **balenaEtcher** para gravar a imagem no cartão SD.
   - **Raspberry Pi Imager**: [Download aqui](https://www.raspberrypi.org/software/).
   - **balenaEtcher**: [Download aqui](https://www.balena.io/etcher/).

4. Insira o cartão SD no leitor de seu computador e siga as instruções da ferramenta para gravar a imagem no cartão.

### 2. Habilitar SSH

Depois de gravar a imagem no cartão SD, precisamos garantir que o SSH esteja habilitado para que possamos acessar remotamente a Raspberry Pi.

1. Abra a partição **boot** no seu computador (essa partição é visível no Windows e macOS).
2. Crie um arquivo vazio chamado **`ssh`** (sem extensão). Isso ativará o SSH automaticamente na próxima inicialização da Raspberry Pi.
   - No Windows: Crie o arquivo através do **Bloco de Notas** ou outro editor de texto e salve-o como **ssh** (certifique-se de que ele não tenha extensão `.txt`).

### 3. Configurar o Wi-Fi

1. Ainda na partição **boot**, crie um arquivo chamado **`wpa_supplicant.conf`** e insira o seguinte conteúdo, substituindo pelo nome da sua rede Wi-Fi (SSID) e senha (PSK):

   ```bash
   country=BR
   ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
   update_config=1

   network={
       ssid="NOME_DA_REDE"
       psk="SENHA_DA_REDE"
       key_mgmt=WPA-PSK
   }
   
2. Salve o arquivo e remova o cartão SD com segurança do computador.

### 4. Iniciar a Raspberry Pi Zero W

1. Insira o cartão SD na Raspberry Pi Zero W.
2. Conecte a fonte de alimentação à Raspberry Pi.
3. Aguarde alguns minutos para que a Raspberry Pi se conecte à rede Wi-Fi.

### 5. Conectar via SSH
Agora que a Raspberry Pi está conectada à rede Wi-Fi, você pode acessá-la remotamente via SSH.

1. No seu computador, abra o Bitvise SSH Client ou um terminal (Prompt de Comando no Windows, por exemplo).
2. Execute o seguinte comando para acessar a Raspberry Pi via nome de host:

   ```bash
   ssh pi@raspberrypi.local

  - Nota: Se você não conseguir se conectar com raspberrypi.local, pode ser que seu roteador tenha atribuído um IP diferente. Nesse caso, verifique o IP da Raspberry Pi no painel do seu roteador ou usando um aplicativo como Fing.

3. Quando solicitado, insira a senha padrão: **raspberry**.

### 6. Atualizar o Sistema
É sempre recomendável garantir que todos os pacotes estejam atualizados. Após conectar via SSH, execute os seguintes comandos:

   ```bash
   sudo apt update
   sudo apt upgrade
   ```

Esses comandos atualizam os pacotes do sistema e garantem que você esteja rodando as versões mais recentes disponíveis.

### 7. Pronto para Usar
Agora sua Raspberry Pi Zero W está configurada no modo Wi-Fi e acessível via SSH. Você pode começar a instalar pacotes, configurar serviços ou usá-la como um dispositivo IoT, servidor ou qualquer outro projeto que desejar.

---

### Considerações Finais
Este tutorial foi criado para oferecer uma maneira rápida e prática de configurar sua Raspberry Pi Zero W. Utilizamos a imagem Raspberry Pi OS (Legacy, 32-bit) devido à sua estabilidade e compatibilidade com o hardware da Raspberry Pi Zero W, algo que versões mais recentes não garantiram consistentemente.

---

## Backup Pessoal da Imagem do Raspberry Pi OS

Este repositório contém o link para o backup da imagem do **Raspberry Pi OS (Legacy, 32-bit)** para Raspberry Pi Zero W.

Link para a imagem: [Google Drive Backup](https://drive.google.com/file/d/1ARpFssfaXqQqfTyeAVscqQLd-_WCvMai/view?usp=sharing)


