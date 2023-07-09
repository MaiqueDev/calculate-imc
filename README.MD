# Código JavaScript para cálculo do IMC

Este é um exemplo de código em JavaScript que calcula o Índice de Massa Corporal (IMC) com base no peso e na altura fornecidos. O código utiliza Promises para processar assincronamente o cálculo do IMC e exibe o resultado no console.

## Instruções para execução do código

Siga as instruções abaixo para executar o código e testar a função `imc(weight, height)`:

1. Certifique-se de ter um ambiente JavaScript adequado para a execução do código, como um navegador web com console ou um ambiente de desenvolvimento JavaScript, como o Node.js.

2. Copie o código JavaScript para um arquivo com a extensão `.js`, por exemplo, `imc.js`.

3. Abra o terminal ou prompt de comando e navegue até o diretório onde o arquivo `imc.js` foi salvo.

4. Execute o arquivo JavaScript usando o ambiente JavaScript de sua escolha. Por exemplo, se você estiver usando o Node.js, execute o seguinte comando:

   ```
   node imc.js
   ```

5. Observe a saída no console, que exibirá o resultado do cálculo do IMC para cada chamada da função `showImc(weight, height)`, juntamente com a situação correspondente.

## Código JavaScript

```javascript
// Função assíncrona para cálculo do IMC
function imc(weight, height) {
  return new Promise((resolve, reject) => {
    if (typeof weight !== 'number' || typeof height !== 'number') {
      reject('Seus argumentos precisam ser do tipo number');
    } else {
      resolve(weight / (height * height));
    }
  });
}

// Função para exibir o IMC e a situação correspondente
function showImc(weight, height) {
  imc(weight, height)
    .then((result) => {
      console.log(`O resultado do IMC é: ${result}.`);

      if (result < 18.5) console.log('Situação: MAGREZA');
      else if (result < 25) console.log('Situação: NORMAL');
      else if (result < 30) console.log('Situação: SOBREPESO');
      else if (result < 40) console.log('Situação: OBESIDADE');
      else console.log('Situação: OBESIDADE GRAVE');
    })
    .catch((err) => {
      console.log(err);
    });

  console.log('Calculando...');
}

// Chamadas de exemplo para testar o código
showImc(71, 1.74);
showImc(48, 1.74);
showImc(71, 'texto');
showImc(82, 1.72);
showImc(120, 1.80);
showImc(71, 1.74);
```

Lembre-se de fornecer valores numéricos adequados para o peso (`weight`) e altura (`height`) ao chamar a função `showImc(weight, height)`. O código realizará o cálculo do IMC para cada chamada e exibirá o resultado no console, juntamente com a situação correspondente ao IMC calculado.