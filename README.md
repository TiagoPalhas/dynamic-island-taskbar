# Dynamic Island na Barra de Tarefas

Mod para o [Windhawk](https://windhawk.net) que coloca a **Dynamic Island** dentro da
barra de tarefas do Windows 11. É um fork do
[Dynamic Island for Windows](https://github.com/devcode90/Dynamic-Island-for-Windows) 1.4.0,
de devcode90 e colaboradores. Mantém todos os módulos e animações do original
(mídia, letras, clima, calendário, monitor de hardware, alertas) e passa a funcionar
encaixado na barra, como o mod Island Media Controls.

*English: a Windhawk mod that docks the Dynamic Island inside the Windows 11 taskbar.
Fork of Dynamic Island for Windows 1.4.0 by devcode90.*

## O que muda em relação ao original

- **Encaixada na barra:** segue a janela real da barra de tarefas, fica centralizada
  na altura dela e desliza junto quando a barra se oculta automaticamente.
- **Sempre por cima da barra:** um gancho de foco (`EVENT_SYSTEM_FOREGROUND`) traz a
  ilha de volta na hora em que a barra é clicada, então ela não some atrás do vidro da barra.
- **Controles de mídia na ilha recolhida:** capa, título, artista e os botões
  ⏮ ⏯ ⏭. Clique nos botões para controlar a música e no resto da ilha para expandir.
- **Abas em ordem de chegada:** a ilha de mídia fica fixa à esquerda e alertas novos
  (área de transferência, volume, notificações, Caps Lock...) entram à direita.
- **Tamanho da barra:** as abas recolhidas têm no máximo a altura da barra, e os textos
  de status cabem traduzidos ("Ligado/Desligado").
- **Independente:** tem ID próprio (`dynamic-island-taskbar`) e não precisa do mod original.

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

## Configurações padrão

Já vem pronto para a barra; os outros valores são os do original.

| Configuração | Valor | Motivo |
|---|---|---|
| Position | Bottom Left | Coloca a ilha na barra de tarefas |
| Offset Y | 0 | A ilha se centraliza sozinha; use só como ajuste fino |
| Size scale | 0.8x | Cabe na altura da barra |
| Expand on hover | Desligado | Expande ao clicar, para dar tempo de usar os botões ⏮ ⏯ ⏭ |
| Do Not Disturb alert | Desligado | Menos alertas na barra |

## Limitações

- A ilha é uma janela própria sobre a barra, não um elemento dentro dela. Não empurra
  os ícones da barra e, em casos raros, pode piscar por um quadro ao clicar na barra.
- Em capturas com a Ferramenta de Captura (Win+Shift+S), a ilha aparece atrás da barra.
  Isso é de propósito no original, para não cobrir a tela de recorte.
- Feito para a barra embaixo; com a barra em outro lado, usa o posicionamento original.

## Créditos

- **[Dynamic Island for Windows](https://github.com/devcode90/Dynamic-Island-for-Windows)**,
  de devcode90 e colaboradores (créditos completos no cabeçalho do mod), sob licença MIT.
- Adaptação para a barra de tarefas: **[Tiago Palhas](https://github.com/TiagoPalhas)**.

## Licença

[MIT](LICENSE)
