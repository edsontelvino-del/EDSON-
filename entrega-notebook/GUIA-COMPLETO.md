# FaresVision 2.0 — Android e teste local com PDF/OCR

Painel baseado no material fornecido pelo usuário. Mantém identificação, sinais vitais, antropometria, oftalmologia OD/OE, retinografias, anexos, resultados laboratoriais, mapa corporal, histórico, fichas, backup, impressão e relatórios. A comparação entre exames antigos e novos continua ausente, como no ZIP original. Android usa os mesmos arquivos e lógica do painel, com controles nativos para selecionar e exportar arquivos.

## Entregas

- **FaresVision-Android-Teste.apk**: aplicativo de teste, Android 8.0/API 26 ou superior, com Android System WebView atualizado. Assinado com chave de desenvolvimento; não publicado na Play Store.
- **FaresVision-Teste-Android-PDF.html**: demonstração em arquivo único para Edge/Chrome modernos, com PDF.js, OCR e modelo de português incorporados. Salve e abra no navegador. O comportamento do protocolo `file://` varia conforme políticas do navegador; neste ambiente ele é bloqueado administrativamente, por isso a demonstração foi testada servida localmente.
- **exame-ficticio.pdf** e versão digitalizada: dados exclusivamente fictícios para testar a importação. As referências impressas nesses exemplos são fictícias do laudo de teste e não constituem uma tabela universal da OMS.
- Código-fonte, testes e adaptador opcional de IA.

**O ChatGPT desta sessão não dispõe de ferramenta para executar uma interface HTML ou Android interativa dentro da conversa.** O teste interativo abre no navegador ou no Android. Aqui foram executados testes automatizados com navegador real. Não foi realizada validação em aparelho Android físico nem em emulador.

## Abrir o app Android

1. Transfira o APK para um aparelho de teste e abra-o pelo gerenciador de arquivos. Se o Android solicitar, autorize a instalação dessa origem para esse arquivo de teste.
2. Abra **FaresVision Teste**. O painel completo pode ser ampliado com gesto de pinça. **Ajustar tela** reorganiza o conteúdo para leitura no celular; **Painel completo** retorna à apresentação ampla.
3. Cadastre os dados fictícios e use **Salvar**. O histórico e os anexos ficam no armazenamento privado do WebView do app.
4. **Exportar JSON** e **Backup** abrem o seletor Android para escolher o destino. **Imprimir** usa o serviço de impressão do Android, inclusive Salvar como PDF quando disponível.
5. Desinstalar o app ou limpar seus dados pode apagar as fichas. Exporte backups antes dessas ações.

Não há permissão para varrer a pasta Downloads. Primeiro baixe o PDF no aparelho e depois o selecione na aba **Exame de Sangue**. O app acessa somente o arquivo que você escolher.

## Preenchimento automático a partir de PDF

1. Em **Exame de Sangue**, selecione um PDF, ou use **Baixar PDF de exemplo**.
2. A leitura começa localmente. PDFs textuais usam extração de texto; páginas sem texto passam por OCR em português. Nenhum documento é enviado a serviços externos nessa etapa.
3. O diálogo mostra parâmetro, resultado, unidade, limites extraídos, página e trecho original. Linhas ambíguas e não reconhecidas permanecem disponíveis para conferência. A leitura pode omitir ou confundir resultados em layouts complexos; não suponha que todos os itens foram extraídos.
4. O teste usa convenção numérica pt-BR: vírgula decimal e ponto com grupos de três dígitos como milhar. O diálogo mostra também o número interpretado. Se o laudo usar outra convenção, reescreva o resultado e os limites sem separador de milhar antes de confirmar. Corrija os dados, confirme a conferência e clique em **Preencher painel com resultados conferidos**. É possível acrescentar resultados ou substituir a tabela existente.
5. O painel e o mapa são atualizados. Clique na coluna **Referência / fonte** para corrigir limites do laboratório. Mudar a unidade invalida a referência antiga até nova conferência.

A confirmação é obrigatória porque valores de OCR ou tabelas podem ser lidos incorretamente. A extração não é uma validação clínica. PDF protegido precisa ser desbloqueado pelo responsável antes da importação. Limites: 25 MB por PDF, até 20 páginas, até 8 páginas com OCR e até 500 resultados. OCR tem limites de tempo e depende da qualidade da digitalização e do aparelho.

## Análise local e referências

Não existe uma tabela universal da OMS cobrindo todos os exames da imagem. O sistema não atribui à OMS faixas de LDL, HDL, creatinina, TSH, vitamina D etc.

- Quando informada, a referência do laboratório, na unidade e contexto do paciente, é usada e identificada como fonte do laudo.
- O catálogo inicial inclui critérios explícitos para hemoglobina/anemia, glicose plasmática em jejum, HbA1c, pressão arterial e IMC, com fontes e restrições visíveis em **Contexto e fontes da análise local**.
- Critérios dependentes de idade, sexo, gestação, material, jejum ou método permanecem sem classificação quando faltam dados.
- Os limites OMS de glicose/HbA1c selecionados são critérios específicos de hiperglicemia/diagnóstico e não avaliam todas as causas de alteração. O limiar de hemoglobina selecionado avalia anemia, não uma faixa superior normal. Uma pressão isolada não diagnostica hipertensão.
- Demais campos sem critério aplicável aparecem como **Não avaliado**, **Falta contexto** ou registro profissional; não são considerados normais pela ausência de regra.
- Cada parâmetro sinalizado recebe uma especialidade a considerar e a razão da sinalização. Não são diagnósticos nem encaminhamentos automáticos. Exemplos: creatinina → Nefrologia; perfil lipídico → Cardiologia; TSH → Endocrinologia; hemoglobina → Hematologia. Marcadores não catalogados com referência alterada sugerem avaliação inicial em Clínica Médica.
- O mapa associa os dados visualmente a regiões e sistemas. Não localiza doença nem interpreta retinografia.

Fontes do catálogo inicial (as URLs e a aplicação clínica devem ser revisadas pela equipe responsável antes de uso assistencial):

- OMS, *Guideline on haemoglobin cutoffs to define anaemia*, 2024: https://www.who.int/publications/i/item/9789240088542
- OMS/IDF, *Definition and diagnosis of diabetes mellitus and intermediate hyperglycaemia*, 2006: https://iris.who.int/handle/10665/43588
- OMS, *Use of glycated haemoglobin (HbA1c) in the diagnosis of diabetes mellitus*, 2011: https://iris.who.int/handle/10665/70523
- OMS, *Hypertension*: https://www.who.int/news-room/fact-sheets/detail/hypertension
- OMS, *Obesity and overweight*: https://www.who.int/news-room/fact-sheets/detail/obesity-and-overweight

## IA: integração preparada, desativada

Conforme a escolha do usuário, o teste é local. Não há modelo de IA ativo nem credencial de provedor configurada. Extração de PDF, OCR e comparação de referências funcionam sem IA generativa. A interface identifica esse modo claramente.

O adaptador de servidor está em `server/local_server.py`; veja `server/README.md`. Por padrão `/api/analyze` retorna HTTP 503 e `mode: disabled`. Para ativar futuramente são necessários provedor autorizado, chave no servidor, modelo, HTTPS e autenticação. O painel exige autorização explícita antes de qualquer envio. Nunca coloque chave do provedor no APK/HTML. A resposta externa não substitui os resultados originais e é invalidada quando a ficha muda.

A integração foi preparada e seus bloqueios locais testados; não foi validada com um provedor real nem implantada. O servidor incluído é de desenvolvimento e não deve ser exposto em produção sem controles adicionais.

## Segurança e validação clínica

Use dados fictícios nesta entrega. Não há autenticação de pacientes/profissionais, auditoria clínica, criptografia própria do banco/backup, validação diagnóstica nem homologação assistencial. O Android usa o isolamento de dados do app, mas isso não substitui um projeto de proteção de dados e controle de acesso. Backups contêm os dados e anexos completos; guarde-os em local protegido. A validade das referências, o desempenho de extração e as recomendações precisam de validação clínica independente antes de uso com pacientes reais.

## Desenvolvimento e testes

```sh
npm ci
npm test
npm run test:ui
npm run test:pdf
python3 -m unittest discover -s tests -p 'test_server.py'
python3 server/local_server.py --port 8765
```

Os testes UI usam `/usr/bin/chromium`; adapte o caminho para sua instalação. A versão servida abre em `http://127.0.0.1:8765/index.html` no próprio computador. Não é um endereço de acesso remoto nem um link para executar no ChatGPT.

- `tools/build-browser.py` gera a edição HTML única, com modelos incorporados, em `dist/entrega`. A variável opcional `FARES_OUTPUT_DIR` altera o diretório de saída.
- `tools/prepare-android-assets.py` copia o painel e os recursos offline para o app.
- `android/build-apk.sh` compila um APK sem Gradle, usando ferramentas oficiais Android 35 e compilador Java. Configure `FARES_ANDROID_SDK` se o SDK estiver em outro local. Requer módulo `jdk.compiler`, `keytool`, SDK platform 35 e build-tools 35.0.0. A chave gerada é apenas de teste e não deve ser usada para produção.
- O fluxo desktop Electron também permanece no código; `npm start` exige ambiente gráfico. As novas dependências e recursos estão incluídos na configuração de empacotamento, mas não foi produzido outro executável Windows nesta entrega.

Verificado: testes de critérios e parser, fluxo legado do painel, importação real de PDF textual, OCR real em português em PDF digitalizado, conferência obrigatória, fontes, sugestões por parâmetro, persistência, invalidação de unidades, layout móvel, HTML único e bloqueios do servidor de IA. APK compilado e assinatura v2/v3 verificada. Não verificado: execução em aparelho/emulador Android, IA com provedor real, publicação em loja, diagnóstico clínico, layouts arbitrários de todos os laboratórios e execução HTML sob políticas específicas de cada PC.
