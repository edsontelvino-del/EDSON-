# FaresVision para notebook Windows

Pacote de teste com o painel integrado, importação local de PDF/OCR e histórico. IA generativa desativada. Use dados fictícios.

**[Baixar o pacote para Windows](https://github.com/edsontelvino-del/EDSON-/raw/refs/heads/entrega-notebook/entrega-notebook/FaresVision-PARA-NOTEBOOK.zip)**

Se o navegador abrir a página do ZIP em vez de baixar, use **Download raw file** (ícone de download). O GitHub não precisa visualizar o ZIP para permitir o download. Caso o repositório seja privado, entre com a conta GitHub que tem acesso a ele.

1. Baixe o arquivo `FaresVision-PARA-NOTEBOOK.zip`.
2. No Windows, clique com o botão direito e escolha **Extrair tudo**.
3. Abra a pasta extraída e execute **INICIAR-WINDOWS.cmd**.
4. O iniciador abre o painel no navegador e atende somente conexões do próprio notebook. Mantenha a janela aberta durante o uso. Ele não instala Node.js/Python nem altera políticas de segurança.
5. Alternativa: clique com o botão direito em **PAINEL.html** → **Abrir com → Google Chrome**.
6. Use **EXAME-DE-TESTE.pdf** para testar a importação. Confira os valores antes de confirmar o preenchimento.
7. Exporte uma cópia JSON antes de encerrar. O endereço local usa uma porta temporária; restaure sua cópia ao iniciar outra sessão se o histórico não aparecer.

O painel HTML e os fluxos de PDF/OCR foram verificados em navegador automatizado. O iniciador e o funcionamento nativo neste notebook Windows ainda precisam ser confirmados pelo usuário. A demonstração abre fora do ChatGPT.

Não há tabela universal da OMS para todos os exames. A análise identifica critérios específicos e referências do laboratório, com limitações de contexto. Não constitui diagnóstico nem encaminhamento automático. Veja [o guia completo](GUIA-COMPLETO.md).

A entrega está em uma branch separada; não substitui uma branch principal existente. O pacote não contém chaves de API, credenciais, fichas reais ou chaves de assinatura do aplicativo.
