# AI Fundamentals: Azure Speech Studio & Language Studio Practice

## Objetivo

Este repositório contém anotações e insights obtidos durante a prática aprofundada das ferramentas Azure Speech Studio e Azure Language Studio (Text Analytics). O foco está em desenvolver habilidades práticas na criação de soluções de IA voltadas para voz e linguagem natural.

## Prerequisitos

- Conta Azure ativa
- Permissões para criar recursos nos serviços:
  - Speech Resource (Cognitive Services)
  - Text Analytics Resource (Cognitive Services)
- Ferramentas locais:
  - Azure CLI
  - Python 3.x e SDK "azure-cognitiveservices-speech"
  - Bibliotecas Python: `azure-ai-textanalytics`, `pyaudio` (se necessário)

## Estrutura do Repositório

\`\`\`
/ai-fundamentals-practice
│
├── labs
│   ├── 09-speech
│   │   ├── speech_samples
│   │   └── notes.md
│   └── 06-text-analysis
│       ├── text_samples
│       └── notes.md
│
├── scripts
│   ├── speech_to_text.py
│   ├── text_to_speech.py
│   └── text_analysis.py
│
└── README.md
\`\`\`

## Lab 1: Azure Speech Studio (Speech Fundamentals)

Referência: [Lab 09 - Speech](https://microsoftlearning.github.io/mslearn-ai-fundamentals/Instructions/Labs/09-speech.html)

### Visão Geral

Nesta seção, exploramos os recursos de IA de fala:

- **Speech-to-Text**: transcrição de áudio em texto.
- **Text-to-Speech**: síntese de voz a partir de texto.
- **Custom Speech**: criação e uso de modelos customizados.
- **Speech Translation**: tradução de fala em tempo real.

### Passos Principais

1. **Criar Speech Resource** no portal Azure.
2. **Obter Chave e Endpoint** para autenticação.
3. **Instalar SDK**:
   \`\`\`bash
   pip install azure-cognitiveservices-speech
   \`\`\`
4. **Transcrição de Áudio**:
   - Exemplo de uso de `SpeechConfig`, `AudioConfig` e `SpeechRecognizer`.
   - Gravar áudio localmente ou usar arquivo de exemplo.
5. **Síntese de Voz**:
   - Exemplo com `SpeechSynthesizer` para gerar saída em WAV.
   - Ajustar vozes (`voice_name`) e configurações de saída.
6. **Tradução de Fala**:
   - Configurar `TranslationRecognizer` para traduzir de um idioma para outro.
7. **Insights & Observações**:
   - Latência e qualidade variam conforme a rede e tamanho do áudio.
   - Modelos customizados melhoram precisão em vocabulários específicos.
   - Verificar limites de cotas e custos no portal.

## Lab 2: Azure Language Studio (Text Analytics)

Referência: [Lab 06 - Text Analysis](https://microsoftlearning.github.io/mslearn-ai-fundamentals/Instructions/Labs/06-text-analysis.html)

### Visão Geral

Nesta seção, exploramos o Text Analytics para:

- **Análise de Sentimento**: identificar polaridade de texto.
- **Extração de Frases-chave**: destacar termos relevantes.
- **Reconhecimento de Entidades Nomeadas (NER)**: identificar pessoas, locais, organizações.
- **Detecção de Idioma**: identificar automaticamente a língua do texto.

### Passos Principais

1. **Criar Text Analytics Resource** no portal Azure.
2. **Obter Chave e Endpoint** para autenticação.
3. **Instalar Biblioteca**:
   \`\`\`bash
   pip install azure-ai-textanalytics
   \`\`\`
4. **Código de Exemplo**:
   - Autenticação com `TextAnalyticsClient`.
   - Chamadas para `analyze_sentiment`, `extract_key_phrases`, `recognize_entities`, `detect_language`.
5. **Exemplos de Uso**:
   \`\`\`python
   from azure.ai.textanalytics import TextAnalyticsClient, AzureKeyCredential

   client = TextAnalyticsClient(endpoint, AzureKeyCredential(key))
   documents = ["A Azure Cognitive Services é incrível para IA." ]
   sentiment = client.analyze_sentiment(documents)
   key_phrases = client.extract_key_phrases(documents)
   entities = client.recognize_entities(documents)
   \`\`\`
6. **Insights & Observações**:
   - A qualidade da análise depende do tamanho e clareza do texto.
   - Suporte multilíngue robusto para mais de 20 idiomas.
   - Atenção às cotas de chamadas por segundo para evitar throttling.

## Insights Gerais e Boas Práticas

- **Gerenciamento de Recursos**: Use grupos de recursos para manter organizado. Monitore uso e custo regularmente.
- **Modularização**: Separe scripts por funcionalidade (speech, tts, análise de texto) para facilitar manutenção.
- **Automação**: Considere criar pipelines CI/CD que validem e implantem suas funções de IA.
- **Segurança**: Armazene chaves de forma segura, usando Azure Key Vault sempre que possível.

## Próximos Passos

- Explorar **Custom Neural Voice** para síntese mais natural.
- Testar **Conversational Language Understanding (LUIS)** integrado com o Bot Framework.
- Avaliar **Embeddings** de linguagem para tarefas avançadas de similaridade e recomendação.
- Documentar benchmarks de latência e custo para cada serviço.

---

*Este README é um guia vivo: atualize suas notas e insights conforme aprofunda seu conhecimento nas ferramentas Azure Cognitive Services.*
