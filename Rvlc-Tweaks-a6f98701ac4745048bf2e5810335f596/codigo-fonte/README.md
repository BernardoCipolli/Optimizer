# Rvlc Tweaks

O Rvlc Tweaks é um aplicativo portátil para Windows que reúne monitoramento de hardware, ajustes do sistema e um tutorial guiado. A interface tem temas claro e escuro, fundo animado e modelos 3D que você pode girar com o mouse ou com as setas do teclado.

## Requisitos

- Windows 10 ou 11 de 64 bits em um processador Intel ou AMD.
- Microsoft Edge WebView2 Evergreen Runtime. Se ele estiver ausente, o aplicativo oferece a página de instalação. [Download oficial do WebView2](https://developer.microsoft.com/microsoft-edge/webview2/)

## Como usar

Abra o executável `Rvlc-Tweaks.exe` da publicação do projeto. Se houver uma versão anterior aberta, feche-a primeiro. O aplicativo inicia na aba **Tutorial** e retoma a etapa salva para sua conta do Windows.

| Área | O que você pode fazer |
| --- | --- |
| **Tutorial** | Siga 23 etapas com imagens, instruções e atalhos para as abas do programa. |
| **Otimização** | Acompanhe o uso da CPU, da RAM e do disco. Use **Analisar PC** para identificar os componentes e consultar ajustes indicados. A aba também dá acesso ao Modo de Jogo, ao Game DVR e ao Optimizer. |
| **Mouse** | Abra as propriedades adicionais do mouse para ajustar o ponteiro, os botões e a roda. |
| **Monitor** | Abra a **Tela avançada** para escolher o monitor e ajustar a taxa de atualização. No Windows 11 24H2 ou mais recente, o botão usa o atalho direto. Se o Windows abrir **Sistema → Tela**, selecione **Tela avançada**. |
| **GPU NVIDIA** | Baixe o NVIDIA Profile Inspector, o MSI Utility v3 e os perfis `.nip`. A aba separa os perfis dos arquivos de ajuste e inclui a página do autor do MSI Utility. |
| **Limpeza** | Salve os dois scripts originais na pasta Downloads. |
| **Planos de energia** | Selecione um plano instalado ou importe um arquivo `.pow`. Clique em **Aplicar plano** para ativar o plano escolhido. |
| **PowerShell** | Copie os comandos do WinUtil ou do Windows10Debloater e abra o GitHub dos autores. Consulte a captura do Debloater e o quadro de exemplos das configurações do WinUtil. |
| **CMD** | Consulte DPS, DiagTrack, PcaSvc e SysMain. A seção permite iniciar os serviços listados e também parar o SysMain. |
| **Histórico** | Consulte as alterações registradas e desfaça as operações que o aplicativo oferece para reversão. |

O botão ao lado de cada modelo 3D restaura a vista inicial. O movimento dos modelos e do fundo acompanha a configuração de movimento reduzido do Windows.

## Segurança e dados locais

- **Assinatura digital.** A versão atual está sem assinatura Authenticode. A assinatura oficial depende de um certificado de assinatura de código ou de um serviço autorizado.
- **Permissões.** O aplicativo abre com os privilégios do usuário. Se uma operação de sistema exigir elevação, o Windows solicita a confirmação.
- **PowerShell.** Os botões **Copiar** colocam o comando na área de transferência. Ao rodar um comando no PowerShell, o terminal baixa e executa o script externo.
- **Downloads.** O Optimizer 17.0 vem do GitHub via HTTPS, com verificação de tamanho e SHA-256. O aplicativo salva os arquivos em Downloads e registra a marca de origem do Windows quando a pasta oferece suporte.
- **Scripts de limpeza.** `ResetCacheSystem.bat` e `1._Limpar_Arquivos_de_Lixo.bat` são distribuídos com o conteúdo original. Se executados manualmente, eles podem apagar logs, relatórios de diagnóstico e, no caso de `1._Limpar_Arquivos_de_Lixo.bat`, esvaziar a Lixeira. Leia os scripts antes de usá-los.
- **Preferências e histórico.** O tema, o progresso do tutorial e o histórico ficam em `%LOCALAPPDATA%\Rvlc Tweaks`, criptografados com a proteção de dados da conta do Windows (DPAPI). Use a mesma conta para acessar os dados protegidos.

## Compilar a partir do código-fonte

O projeto usa Go e uma interface HTML, CSS e JavaScript incorporada ao executável por meio do WebView2. Instale o **Go 1.27.4 ou superior** para Windows AMD64 e execute o comando abaixo na pasta que contém o `go.mod`.

```powershell
go build -buildvcs=false -trimpath -ldflags="-H windowsgui -s -w" -o Rvlc-Tweaks.exe .
```

Se alterar o ícone ou o manifesto do Windows, regenere o recurso antes de recompilar.

```powershell
go run github.com/akavel/rsrc@v0.10.2 -arch amd64 -ico app.ico -manifest app.manifest -o app_windows_amd64.syso
```

## Projetos e ferramentas de terceiros

- **Chris Titus Tech WinUtil.** [Repositório oficial](https://github.com/ChrisTitusTech/winutil)
- **Windows10Debloater**, de Sycnex. [Repositório arquivado](https://github.com/Sycnex/Windows10Debloater)
- **Optimizer**, de hellzerg. [Publicação 17.0](https://github.com/hellzerg/optimizer/releases/tag/17.0)
- **NVIDIA Profile Inspector**, de Orbmu2k. [Publicação 2.3.0.12](https://github.com/Orbmu2k/nvidiaProfileInspector/releases/tag/2.3.0.12)
- **MSI Utility v3.** [Publicação no fórum Guru3D](https://forums.guru3d.com/threads/windows-line-based-vs-message-signaled-based-interrupts-msi-tool.378044/)

O pacote de distribuição inclui as licenças dos componentes redistribuídos.

