# strictNullChecks

O compilador do TypeScript possui uma série de configurações, sendo o strictNullChecks uma delas. Neste modo, null e undefined não fazem parte do domínio dos tipos e só podem ser atribuídos a eles mesmos. Com a exceção de undefined que pode ser atribuído a void. Isso pode ser interessante para evitarmos valores nulos e indefinidos em nosso projeto.

Veja o código exemplo. Pode ser que o elemento pai não exista, logo o valor de parentNode será null.

```tsx
const elCartao: HTMLDivElement = <HTMLDivElement> document.querySelector('#cartao_1');
let elPaiDoPai = elCartao.parentElement.parentElement; // [ts] Object is possibly 'null'
```

Solucao

```tsx
const elCartao: HTMLDivElement = <HTMLDivElement> document.querySelector('#cartao_1');
let elPaiDoPai;
if(elCartao.parentElement) {
    elPaiDoPai = elCartao.parentElement.parentElement;
}
console.log(elPaiDoPai);
```
