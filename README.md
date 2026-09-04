# Extração e validação de notas fiscais eletrônicas

Notebook didático mostrando o núcleo do pipeline de extração e validação usado em um sistema real
de conferência automática de notas fiscais (NF-e/DANFE, NFS-e e CT-e) que desenvolvi:

- Extração de texto de PDF (com fallback para OCR) via `pdfplumber` + `pytesseract`.
- Parsing de campos por regex (PDF) e XPath (XML), incluindo o layout nacional da DANFSe v2.0.
- Validação de CNPJ/CPF e chave de acesso pelos algoritmos oficiais de dígito verificador.
- Consumo de APIs públicas — [Minha Receita](https://minhareceita.org) (situação cadastral e
  regime tributário na Receita Federal) e [BrasilAPI](https://brasilapi.com.br) (tabela NCM/Camex
  e tabela IBPT para recálculo do valor aproximado de tributos).
- Regras de negócio que cruzam tudo isso e geram pendências rastreáveis para revisão humana.

**Todo o conteúdo foi adaptado para fins educacionais:** os documentos de exemplo (PDF/XML)
são sintéticos — CNPJs, razões sociais e valores inventados, sem nenhum dado real de cliente.
A lógica de extração e validação, porém, é a mesma usada em produção.

## Como rodar

```bash
pip install pdfplumber httpx
jupyter notebook extracao_notas_fiscais.ipynb
```

(O passo de OCR é opcional e requer `pytesseract` + Tesseract instalado no sistema — não é
executado no fluxo principal do notebook.)
