# Máscaras de Formulário com JavaScript

Projeto simples desenvolvido em **JavaScript puro** para aplicar máscaras automáticas em campos de formulário HTML.

O arquivo contém funções para formatar dados comuns em sistemas brasileiros, como data, CEP, CPF, CNPJ, telefone, porcentagem, mês e ano, horas e valores monetários em reais.

## Funcionalidades

- Máscara para data no formato `dd/mm/aaaa`
- Máscara para CEP no formato `00000-000`
- Máscara para CPF no formato `000.000.000-00`
- Máscara para CNPJ no formato `00.000.000/0000-00`
- Máscara para telefone fixo no formato `(00) 0000-0000`
- Máscara para celular no formato `(00) 00000-0000`
- Máscara para porcentagem
- Máscara para mês e ano no formato `mm/aaaa`
- Máscara para horas e minutos
- Máscara para moeda brasileira no formato `R$ 0,00`

## Tecnologias utilizadas

- HTML
- JavaScript
- Expressões regulares

## Como funciona

O script captura campos do formulário pelo `id` e aplica a formatação automaticamente durante a digitação do usuário, usando o evento `input`.

Exemplo:

```javascript
var campoData = document.getElementById('id_data');

campoData.addEventListener('input', function () {
    this.value = mascaraData(this.value);
});

´´´
A função remove caracteres que não são números e reorganiza o valor no formato desejado.

```javascript
function mascaraData(data) {
    data = data.replace(/\D/g, '');

    if (data.length > 2) {
        data = data.replace(/^(\d{2})(\d)/g, '$1/$2');

        if (data.length > 5) {
            data = data.replace(/^(\d{2})\/(\d{2})(\d{1,4})$/, '$1/$2/$3');
        }
    }

    return data;
}

´´´



