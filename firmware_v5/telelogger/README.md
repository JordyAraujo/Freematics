# Alterações na versão:

## config.h:

Foram adicionadas duas constantes, SHOULD_OBD_LOG e SHOULD_GPS_LOG, que
definem se os dados do OBD e do GPS devem ser salvos, respectivamente.

## telelogger.h

As funções de log foram alteradas de acordo com a formatação desejada.
Notar que o novo formato não se adequa ao recebido no
[hub do freematics](http://hub.freematics.com).
Isso acontece pois o servidor espera receber os dados no formato [PID:valor],
enquanto esta versão envia apenas [valor:] (':' é o separador de coluna).
Foi adicionada também uma nova função log(char * name) em CStorage, que é
usada para salvar a primeira linha na tabela.
A função timestamp foi alterada para salvar no formato h:m:s:ms. Notar
também que o caractere de nova linha é adicionado antes do timestamp, para
garantir que ele seja o primeiro dado impŕesso.
A linha [m_file.write('\n');] foi removida. Uma nova linha é criada
na tabela sempre que o timestamp é salvo, não sendo mais necessária a
criação em outro momento.

## telelogger.ino

Foram adicionadas constantes de referência para o os cálculos de emissão
(MAF e MAP). Seus valores são os próximos depois da [lista de PIDs](https://en.wikipedia.org/wiki/OBD-II_PIDs#Service_01).
obdData[] foi atualizado para utilizar os PIDs que precisamos.
O struct PID_LIST foi criado para que possamos listar os PIDs (byte pid)
que devem ser salvos na tabela (bool log) e como eles devem ser salvos (char name[20]).
Foram adicionadas duas constantes, shouldOBDLog e shouldGPSLog, que
definem se os dados do OBD e do GPS devem ser salvos, respectivamente (ver config.h).

* ### processOBD:
    Para formatar a tabela, foram criados dois laços que percorrem PIDLog e GPSLog
apenas uma vez e salva o valor do atributo name se o valor do atributo log for true.
O primeiro dado a ser salvo é o timestamp, que começa uma nova linha antes de ser salvo.
A partir disso, um novo laço percorre obdData enquanto outro percorre PIDLog.
Eles então checam se existe um correspondente àquele PID e se ele deve ser salvo.
Se o PID for usado para calcular outro (MAF e MAP), então é checado se o PID a ser calculado
deve ser salvo. Ele só é calculado se necessário, e então é salvo.

A checagem antes do salvamento é feita para cada PID. Isso inclui os dados calculados e
extraídos fora do processOBD(), como GPS e tensão da bateria. Portanto, apenas os PIDs
com atributo log == true em OBDLog e GPSLog serão salvos.
A chamada da função processGPS (dentro de process) foi movida para depois do salvamento
da temperatura por questões de ordenação.