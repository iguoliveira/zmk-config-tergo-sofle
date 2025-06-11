# Firmware Tergo Sofle Wireless (ZMK) - Tergo Teclados

Esta é a pasta do código-fonte do _firmware_ do [teclado Tergo Sofle](https://tecladoergonomico.com.br/) na versão sem fio (wireless).

Caso queira baixar a versão mais recente do _firmware_, visite os releases [clicando aqui](https://github.com/TergoTeclados/zmk-config-tergo-sofle/releases).

Caso tenha chegado aqui por acidente, visite a [documentação oficial do Tergo Sofle](https://github.com/TergoTeclados/Tergo-Sofle-Documentation).

## Por onde começar

Configure seu ambiente para customização do código-fonte e compilação vendo [essa nossa documentação](https://github.com/TergoTeclados/Tergo-Sofle-Documentation/blob/main/guias/especifico_versao_wireless/COMO_MODIFICAR_CODIGO_FONTE.md#tergo-sofle---manual-de-modifica%C3%A7%C3%A3o-do-firmware).

Então, leia o [tópico abaixo](#visão-geral) para entender um pouco sobre cada pasta desse repositório.

Por fim, para gravar o firmware no seu teclado, leia [esse nosso guia](https://github.com/TergoTeclados/Tergo-Sofle-Documentation/blob/main/guias/especifico_versao_wireless/COMO_ATUALIZAR_FIRMWARE.md#manual-de-atualiza%C3%A7%C3%A3o-do-firmware---vers%C3%A3o-wireless).

## Dicas de customizações a fazer

### Mudar tempo para o teclado dormir

- Modifique a variável `CONFIG_ZMK_IDLE_SLEEP_TIMEOUT` do [config/sofle.conf](config/sofle.conf).

Calcule de forma simples com base nos minutos que quer que ele demore e coloque o valor em milisegundos.

> [!TIP]
>
> Exemplo: 15 minutos = `15 * 60 (segundos) * 1000 (mili)` = 900000

### Outros

> [!INFO]
>
> Outras sugestões de customizações podem surgir com o tempo e conforme demanda.
>
> Nos notifique conforme precisar.

## Entendendo melhor: o que é o firmware ZMK

O firmware ZMK não espera que você modifique o código-fonte dele em si, mas sim crie uma configuração para o seu teclado, que é o caso deste repositório.

A partir dessa configuração você customiza seu teclado.

## Resumo sobre as pastas deste repositório

### Configurações gerais

A pasta [config](./config/) possui a configuração e customizações do teclado.

Você irá querer customizar o layout e funcionalidades no arquivo [config/sofle.keymap](./config/sofle.keymap), que possui diversos comentário para te ajudar.

Além disso, há configurações que são feitas no [config/sofle.conf](./config/sofle.conf), como o tempo para o teclado entrar em modo de descanso.

### Shields

Na pasta [boards/shields](./boards/shields/) você encontra "shields".

"Shields" são customizações adicionais que originam do hardware.

Nela você encontrará as shields:
- `dongle_display`, que configura uma tela para o receptor;
- `sofle`, que cria as **metades** do teclado.

## O coração do seu teclado é o receptor (dongle)

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

## Outros

A pasta `.github` contém configurações que fazem com que uma "action" para compilar o firmware seja executada automaticamente ao dar push no repositório.

O arquivo [build.yaml](./build.yaml) especifica o que deve ser compilado e com quais configurações.
