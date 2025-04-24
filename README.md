# Firmware Tergo Sofle Wireless (ZMK) - Tergo Teclados

Esta é a pasta do código-fonte do _firmware_ do [teclado Tergo Sofle](https://tecladoergonomico.com.br/) na versão sem fio (wireless).

Caso queira baixar a versão mais recente do _firmware_, visite os releases [clicando aqui](https://github.com/TergoTeclados/zmk-config-tergo-sofle/releases).

Caso tenha chegado aqui por acidente, visite a [documentação oficial do Tergo Sofle](https://github.com/TergoTeclados/Tergo-Sofle-Documentation).

## Por onde começar

Configure seu ambiente para customização do código-fonte vendo [essa nossa documentação](https://github.com/TergoTeclados/Tergo-Sofle-Documentation/blob/main/guias/especifico_versao_wireless/COMO_MODIFICAR_CODIGO_FONTE.md#tergo-sofle---manual-de-modifica%C3%A7%C3%A3o-do-firmware).

Então, leia o [tópico abaixo](#visão-geral) para entender um pouco mais sobre o firmware.

Por fim, para gravar o firmware no seu teclado, leia [esse nosso guia](https://github.com/TergoTeclados/Tergo-Sofle-Documentation/blob/main/guias/especifico_versao_wireless/COMO_ATUALIZAR_FIRMWARE.md#manual-de-atualiza%C3%A7%C3%A3o-do-firmware---vers%C3%A3o-wireless).

## Visão Geral

### Firmware ZMK

O firmware ZMK não espera que você modifique o código-fonte dele em si, mas sim crie uma configuração para o seu teclado, que é o caso deste repositório.

A partir dessa configuração você customiza seu teclado.

### Como funciona

#### Configurações gerais

A pasta [config](./config/) possui a configuração e customizações do teclado.

Você irá querer customizá-lo pelo arquivo [config/sofle.keymap](./config/sofle.keymap).

#### Shields

Na pasta [boards/shields](./boards/shields/) você encontra "shields".

"Shields" são customizações adicionais que originam do hardware.

Nela você encontrará a shield `dongle_display` que configura uma tela para o receptor e `sofle`, que cria as partes do teclado.

### O coração do seu teclado é o receptor (dongle)

Para você entender a essência dos arquivos presentes nesse repositório:

> [!IMPORTANT]
>
> As configurações gerais do teclado são aplicadas no arquivo `config/sofle.keymap`, como falado antes, e não na pasta `boards/shields/sofle`.
>
> Isso pois essa configuração é colocada no dongle em si.
>
> Quem interpreta todos sinais das partes do teclado é o receptor.
>
> As partes do teclado são meramente "shields", que enviam ao receptor os sinais de digitação.
>
> É o receptor quem processa esses sinais.
>
> É por isso que a maioria das customizações que você realizar no `sofle.keymap` que adicionem funcionalidades não necessitam da regravação do firmware nas partes do teclado, e sim apenas no receptor.

### Outros

A pasta `.github` contém configurações que fazem com que uma "action" para compilar o firmware seja executada automaticamente ao dar push no repositório.


