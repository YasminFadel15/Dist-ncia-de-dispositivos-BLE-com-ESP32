
# Distância de Dispositivos BLE com ESP32

## Objetivo

O projeto visa reconhecer dispositivos BLE (Bluetooth Low Energy) em um raio de 10 metros utilizando a placa ESP32 e estimar a distância dos mesmos em relação à placa.

#### Observações: Este projeto foi implementado no Linux, utilizando a distribuição Fedora versão 23.

## Ferramentas Utilizadas

- Arduino IDE: Para desenvolvimento e upload do código na placa ESP32.
- Broker Mosquitto: Para comunicação via protocolo MQTT.
- MQTT X: Ferramenta cliente para testar e monitorar mensagens MQTT.
- Linguagem: C++

## Informações sobre o ESP32
 ![ESP32 WROOM](https://docs.espressif.com/projects/esp-idf/en/stable/esp32/_images/esp32-devkitC-v4-pinout.png)


## Instalações e Configurações

### Arduino IDE

- Download: Baixe o Arduino IDE no site oficial.
- Configuração: Adicione suporte à placa ESP32:
    - Acesse: File > Preferences.
    - Adicione o link ```https://dl.espressif.com/dl/package_esp32_index.json``` no campo "Additional Board Manager URLs".
    - Acesse Tools > Board > Board Manager e instale o pacote esp32 do autor Espressif.

### Mosquitto
- Abra o terminal e digite o comando:

```
sudo dnf install mosquitto
```
- Abra o arquivo ```mosquitto.conf``` com o comando:
```
mosquitto -c /etc/mosquitto/mosquitto.conf
```
- Digite as seguintes linhas:
```
listener 1883
allow_anonymous true
```
- Assim, será possível utilizar a porta 1883 sem precisar de um usuário ou senha.
- A seguir, estão alguns comandos que podem ser úteis na utilização do Mosquitto:
    - Verificar se a porta 1883 está aberta: ```sudo ss -tuln | grep 1883``` 
    - Habilitar o Mosquitto: ```sudo systemctl enable mosquitto``` 
    - Iniciar o Mosquitto: ```sudo systemctl start mosquitto```
    - Parar o Mosquitto: ```sudo systemctl stop mosquitto``` 
    - Verificar logs do Mosquitto: ```sudo journalctl -u mosquitto```
    
### MQTT X
- Download: Baixe o MQTT X no site oficial.

## Desenvolvimento
- Carregar o código na ESP32:
        Abra o Arduino IDE.
        Conecte a ESP32 ao seu computador via USB.
        Selecione a placa correta em Tools > Board > ESP32 Dev Module.
        Selecione a porta correta em Tools > Port.
        Carregue o código.

    Configuração do Mosquitto:
        Certifique-se de que o serviço Mosquitto está rodando.

    Utilização do MQTT X:
        Configure o cliente MQTT X para se conectar ao broker Mosquitto.
        Subscrição nos tópicos relevantes para monitorar os dados enviados pela ESP32.
