# Arquivo de configurações:

## CSV Logging Configuration:
---

### SHOULD_OBD_LOG e SHOULD_GPS_LOG:

    Definem respectivamente se os dados do OBD e do GPS deverão ser salvos.

## Circular Buffer Configuration:
---

### BUFFER_SLOTS e BUFFER_LENGTH:

    BUFFER_SLOTS define a quantidade de slots de tamanho BUFFER_LENGTH bytes a serem armazenados no buffer.

### SERIALIZE_BUFFER_SIZE:

    Esta variável precisa de mais investigações.

## Configuration Definitions:
---

    Definições de configuração de dispositivo de rede, acelerômetro, armazenamento, protocolo e método de requisição.

## OBD-II configurations:
---

### ENABLE_OBD:

    Define se o OBD será utilizado.

### MAX_OBD_ERRORS:

    Quantidade de erros de OBD permitidos antes de entrar em standby.

## Networking Configurations:
---

### NET_DEVICE:

    Define o dispositivo de rede a ser utilizado. (NET_WIFI para utilizar Wifi e NET_SIM5360 para utilizar o 3G brasileiro).

### WIFI_SSID e WIFI_PASSWORD:

    Nome e senha da rede WiFi. Se NET_DEVICE não estiver definido como NET_WIFI, estes valores serão desconsiderados.

### CELL_APN:

    Endereço APN da operadora.

### SERVER_HOST e SERVER_PROTOCOL:

    Endereço do host e protocolo a ser utilizado no servidor.

### SIM_CARD_PIN:

    PIN do cartão SIM, caso necessário.

### SERVER_METHOD e SERVER_PATH:

    Método de requisição e caminho da api no servidor.

### SERVER_PORT:

    Porta utilizada pelo servidor.

### WIFI_MESH_ID e WIFI_MESH_CHANNEL:

    ID e canal da Wifi Mesh (a ser estudado).

### WIFI_AP_SSID e WIFI_AP_PASSWORD:

    ID e senha do Acess Point, se necessário.

### MAX_CONN_ERRORS_RECONNECT:

    Número máximo de erros de conexão antes de tentar reconectar.

### MAX_CONN_TIME:

    Não encontrei nenhuma referência a MAX_CONN_TIME no código.

### DATA_RECEIVING_TIMEOUT:

    Define o intervalo esperado para recebimento dos dados do servidor.

### SERVER_SYNC_INTERVAL:

    Define o tempo máximo esperado para sincronização com o servidor.

### STATIONARY_TIME_TABLE e SENDING_INTERVAL_TABLE:

    O intervalo para enviar dados ao servidor é definido pelo tempo em que o veículo se encontra estacionário.
> Por exemplo,
> Se definirmos STATIONARY_TIME_TABLE = {30, 60, 180} e SENDING_INTERVAL_TABLE = {0, 2000, 5000}, o intervalo de envio será 0 ms quando o tempo estacionário t < 30s, será de 2000 ms se 30 < t < 60 e 5000 se t > 60.

### DATASET_INTERVAL:

    Tempo mínimo de cada ciclo de processamento de dados (antes de inicializar a rede para enviá-los).
    Depois de processar os dados do OBD e do GPS, existe o delay de t ms, onde t = DATASET_INTERVAL - tempo decorrido no ciclo.

### PING_BACK_INTERVAL:

## Data storage configurations:
---

### STORAGE:

    Define o método de armazenamento de dados.

## MEMS sensors:
---

### ENABLE_ORIENTATION:

    Define se a orietação por acelerômetro será utilizada.

### MEMS_MODE:

    Define o modo do acelerômetro (a ser estudado).

## GPS:
---

### ENABLE_GPS:

    Define se o GPS será utilizado.

### GPS_SERIAL_BAUDRATE:

    Define a Baudrate utilizada pelo GPS.

### GPS_MOTION_TIMEOUT:

    Não encontrei uso para GPS_MOTION_TIMEOUT. A única referência a ela é num #if 0 que nunca acontece.

## Standby/wakeup:
---

### RESET_AFTER_WAKEUP:

    Define se o dispositivo deve reiniciar (1) ou não (0) depois de sair de Standby.

### MOTION_THRESHOLD:

    Limiar de aceleração definido em G's (usado para identificar se há movimento no carro a partir do acelerômetro)

### JUMPSTART_VOLTAGE:

    Limiar de tensão da bateria para sair do modo de Standby.

## Additional features:
---

### ENABLE_HTTPD:

### ENABLE_OLED:

### CONFIG_MODE_TIMEOUT:

### PIN_SENSOR1 35:

### PIN_SENSOR2 36:

### COOLING_DOWN_TEMP: