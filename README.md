# Dynamic Island na Barra de Tarefas

Mod para o [Windhawk](https://windhawk.net) que coloca a **Dynamic Island** dentro da
barra de tarefas do Windows 11. É um fork do
[Dynamic Island for Windows](https://github.com/devcode90/Dynamic-Island-for-Windows) 1.4.0,
de devcode90 e colaboradores. Mantém todos os módulos e animações do original
(mídia, letras, clima, calendário, monitor de hardware, alertas) e, desde a 2.0.0,
funciona como parte da própria barra.

*English: a Windhawk mod that builds the Dynamic Island into the Windows 11 taskbar.
It runs inside Explorer and its window is owned by the taskbar.
Fork of Dynamic Island for Windows 1.4.0 by devcode90.*

## O que muda em relação ao original

- **Parte da barra** (2.0.0): o mod roda dentro do `explorer.exe` que tem a barra de
  tarefas, e a janela da ilha pertence à janela da barra.
  - A ilha fica logo acima da barra. Quando o Explorer levanta a barra, a ilha volta
    para cima dela no mesmo instante, avisada pela própria thread da barra.
  - Jogos e vídeos em tela cheia cobrem a ilha junto com a barra.
  - A ilha continua visível na Espiada (ao passar o mouse sobre a miniatura de um app).
  - Volta sozinha quando o Explorer reinicia ou recria a barra.
  - Desligar o mod não derruba a barra: as threads seguram o mod carregado até terminar.
- **Encaixada na barra:** segue a janela real da barra de tarefas, fica centralizada
  na altura dela e desliza junto quando a barra se oculta automaticamente.
- **Números com ponto em qualquer idioma** (2.0.0): o tamanho da ilha, o clima e as
  letras são lidos no formato com ponto. No Explorer em português, "0.8" virava 0 e
  a ilha ficava da altura da barra.
- **Menos uso do rádio Bluetooth** (1.2.1): a bateria do headset é lida só escutando
  (busca passiva), a cada 10 minutos (2 com a aba aberta), para não cortar o áudio
  em adaptadores Bluetooth 4.0.
- **Controles de mídia na ilha recolhida:** capa, título, artista e os botões
  ⏮ ⏯ ⏭. Clique nos botões para controlar a música e no resto da ilha para expandir.
- **Abas em ordem de chegada:** a ilha de mídia fica fixa à esquerda e alertas novos
  (área de transferência, volume, notificações, Caps Lock...) entram à direita.
- **Tamanho da barra:** as abas recolhidas têm no máximo a altura da barra, e os textos
  de status cabem traduzidos ("Ligado/Desligado").
- **Independente:** tem ID próprio (`dynamic-island-taskbar`) e não precisa do mod original.
- **Aba Bateria** (1.1.0): mostra a bateria do mouse **BK-R1X** e do headset **QCY H3**,
  com barra que fica âmbar abaixo de 25% e vermelha abaixo de 10%.
  - O mouse é lido pelo comando HID do próprio fabricante.
  - O headset é lido pelo anúncio BLE que ele mesmo transmite (1.2.0), de 1 em 1% e
    com indicação de carregamento, sem abrir conexão com o fone. Se o anúncio não
    chegar, usa uma conexão RFCOMM própria com o fone (de 10 em 10%), que funciona
    mesmo com o Hands-Free (viva-voz) desligado e não cria dispositivo de áudio de chamada.
  - Mouse **VICTORY VT-883** (1.2.0), no receptor YICHIP: aparece como conectado quando
    o receptor está no PC. Esse mouse não envia a bateria ao receptor.
  - Mostra só os aparelhos conectados (1.2.0). Uma configuração permite mostrar
    também os desconectados.
- **Bateria certa no aviso de conexão** (1.2.0): o cartão "Bluetooth Conectado/Desconectado"
  do QCY H3 usa a leitura real do fone. Com o Hands-Free desligado, o valor que o
  Windows guarda fica congelado.
- **Aviso de bateria baixa** (1.1.0): quando o mouse ou o headset chega na porcentagem
  escolhida (padrão 10%), aparece um aviso que pulsa suavemente em vermelho. O número de
  pulsos também é configurável (padrão 1).
- **Configurações em português** (1.1.0): todos os nomes e descrições das configurações
  foram traduzidos para português do Brasil.

Cada alteração no código está marcada com um comentário `Local patch`.

## Requisitos

- Windows 11 com a barra de tarefas **embaixo** e os ícones **centralizados**
  (se estiverem à esquerda, a ilha cobre o botão Iniciar)
- [Windhawk](https://windhawk.net), que já traz o compilador

## Instalação

1. Baixe [`dynamic-island-taskbar.wh.cpp`](dynamic-island-taskbar.wh.cpp).
2. No Windhawk, clique em **Criar novo mod** (*Create a New Mod*).
3. Abra o arquivo no Bloco de Notas, copie tudo (`Ctrl+A`, `Ctrl+C`) e cole no editor do
   Windhawk, substituindo o exemplo (`Ctrl+A`, `Ctrl+V`).
4. Compile com `Ctrl+B` e clique em **Sair do modo de edição**.

Se o **Dynamic Island for Windows** original estiver instalado, desative-o para não
aparecerem duas ilhas.

### Atualizar

Abra o mod no Windhawk → **Detalhes** → **Editar**, cole a versão nova e compile.
Não use "Criar novo mod" de novo, porque isso dá o erro *"Mod id specified in the
source code already exists"*. Depois de recompilar, confira as configurações.
Ao atualizar para a 2.0.0, a barra pode piscar uma vez quando o mod passa a rodar
dentro do Explorer.

## Configurações padrão

Já vem pronto para a barra; os outros valores são os do original.

| Configuração | Valor | Motivo |
|---|---|---|
| Posição | Inferior esquerdo | Coloca a ilha na barra de tarefas |
| Deslocamento Y | 0 | A ilha se centraliza sozinha; use só como ajuste fino |
| Escala de tamanho | 0.8x | Cabe na altura da barra |
| Expandir ao passar o mouse | Desligado | Expande ao clicar, para dar tempo de usar os botões ⏮ ⏯ ⏭ |
| Aviso de Não perturbe | Desligado | Menos alertas na barra |
| Aviso de bateria baixa (mouse e headset) | 10 | Porcentagem do aviso; 0 desliga |
| Pulsos vermelhos do aviso de bateria baixa | 1 | Quantas vezes o aviso pulsa (0 a 10) |
| Mostrar dispositivos desconectados na aba Bateria | Desligado | A aba lista só o que está conectado |

## Limitações

- A ilha pertence à barra, mas ainda é uma janela própria, não um elemento desenhado
  dentro dela. Não empurra os ícones da barra e, ao clicar na barra, pode ficar atrás
  dela por um instante (cerca de 15 a 30 ms) antes de voltar para cima.
- Roda dentro do Explorer: se o mod tiver um erro grave, a barra reinicia (volta
  sozinha em poucos segundos).
- Só para Windows de 64 bits.
- Em capturas com a Ferramenta de Captura (Win+Shift+S), a ilha aparece atrás da barra.
  Isso é de propósito no original, para não cobrir a tela de recorte.
- Feito para a barra embaixo; com a barra em outro lado, usa o posicionamento original.
- A aba Bateria e o aviso de bateria baixa só reconhecem o mouse BK-R1X, o mouse VT-883
  e um headset QCY H3 específico (o endereço Bluetooth está fixo no código). Outros
  aparelhos não aparecem na aba.
- O VT-883 não informa a bateria, então não tem porcentagem nem aviso de bateria baixa.
- O headset anuncia a bateria a cada 2 segundos, mais ou menos. Ao conectar, o aviso
  mostra primeiro o último valor lido e troca pelo atual assim que ele chega.

## Créditos

- **[Dynamic Island for Windows](https://github.com/devcode90/Dynamic-Island-for-Windows)**,
  de devcode90 e colaboradores (créditos completos no cabeçalho do mod), sob licença MIT.
- Adaptação para a barra de tarefas: **[Tiago Palhas](https://github.com/TiagoPalhas)**.

## Licença

[MIT](LICENSE)
