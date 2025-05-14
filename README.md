#**Gerador de Planilha com QR-Codes no Colab**

**Descrição**
Este notebook automatiza, no Google Colab, a coleta de itens (arquivos e pastas) de uma pasta específica do Google Drive, gera links de compartilhamento público e cria QR-Codes para cada item. Ao final, produz uma planilha Excel que inclui os QR-Codes incorporados e um arquivo ZIP contendo todas as imagens geradas.

---

### 1. Título

Gerador de Planilha com QR-Codes a partir do Google Drive no Colab

### 2. Descrição Detalhada

Para empresas de outras áreas, este programa permite extrair rapidamente todos os arquivos e pastas de uma pasta do Google Drive, gerar códigos QR com acesso direto e organizar esses dados em uma planilha de fácil distribuição. É útil para controladoria, logística, RH ou qualquer setor que precise compartilhar pastas e arquivos de forma visual e acessível.

### 3. Pré‑requisitos

* Conta Google com acesso ao Google Drive onde está a pasta‑mãe.
* Permissão de leitura/escrita nessa pasta.
* Acesso ao Google Colab (gratuito).

### 4. Tecnologias Utilizadas

* **Google Colab**: ambiente Python na nuvem.
* **pandas** e **OpenPyXL/XlsxWriter**: manipulação de dados e geração de Excel.
* **qrcode\[pil]** e **Pillow**: criação e edição de imagens QR.
* **google-api-python-client**: comunicação com a Drive API.

### 5. Estrutura e Fluxo de Implementação

1. **Instalação de Dependências**: pacotes Python instalados com `pip install` — roda apenas na primeira execução.
2. **Autenticação do Drive**:

   * Monta o Drive no Colab.
   * Executa `auth.authenticate_user()` para conceder permissões ao notebook.
3. **Configuração da API**:

   * Cria o cliente da Google Drive API (versão v3).
4. **Definição da Pasta‑Mãe**:

   * O usuário insere o `parent_id` (ID da pasta no Drive).
5. **Listagem de Itens**:

   * Busca arquivos e pastas dentro do `parent_id`.
   * Exibe depuração (quantidade e detalhes de cada item).
6. **Geração de Links Públicos**:

   * Verifica e ajusta permissões para `anyone-reader`.
   * Monta a URL de visualização (diferente para arquivos e pastas).
7. **Criação do DataFrame**:

   * Converte a lista de itens em `pandas.DataFrame`.
8. **Geração de QR-Codes**:

   * Para cada linha do DataFrame, gera imagem QR que contém o link.
   * Desenha o nome do item abaixo do QR-Code.
   * Salva cada PNG em uma pasta local.
9. **Validação de Saída**:

   * Verifica se ao menos um QR-Code foi gerado antes de prosseguir.
10. **Geração da Planilha**:

    * Insere, dentro de um arquivo `.xlsx`, o DataFrame e as imagens QR correspondentes.
11. **Compactação**:

    * Cria um arquivo ZIP contendo todas as imagens QR.
12. **Download Automático**:

    * Disponibiliza a planilha e o ZIP para download imediato.

### 6. Como Usar

1. Abra o notebook no Google Colab.
2. Ajuste o valor de `parent_id` para a pasta desejada no Drive.
3. Execute todas as células em ordem (clique em “Run all”).
4. Ao final, baixe `planilha_qr_codes.xlsx` e `qr_codes.zip`.

### 7. Benefícios para o Recrutador

* **Automatização completa** sem necessidade de instalar nada localmente.
* **Visualização imediata** de links por QR-Codes, facilitando a distribuição em materiais impressos ou apresentações.
* **Flexibilidade**: adapta-se a qualquer pasta do Drive, incluindo Shared Drives.

### 8. Possíveis Extensões

* Filtrar tipos específicos de arquivo (PDF, imagens, planilhas).
* Personalizar layout dos QR-Codes (cores, tamanhos).
* Enviar automaticamente planilha por e‑mail.

---

Este README segue boas práticas de clareza, divisão em seções e linguagem voltada a quem não é da área técnica. Fico à disposição para esclarecer dúvidas adicionais.
