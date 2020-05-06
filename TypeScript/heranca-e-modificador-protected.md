# Heranca e Protected

Ao fazer com que uma classe herde o código centralizado em outra classe, prestar atencao se existe alguma propriedade privada dentro do pai.

```tsx
// Pai
class View {
  private _element: Element;

  constructor(selector: string) {
    this._element = document.querySelector(selector);
  }
}

// Filho
class MessageView extends View {
  update(model: string) {
    this._element.innerHTML = this.template(model);
  }

  template(model: string) {
    return `<p class='alert alert-info'>${model}</p>`;
  }
}
```

Perceba que o código acima aponta erro e compilacao. O problema é que propriedades declaradas com o modificador **private** não podem ser acessadas nem mesmo pelas classes filhas. 

Podemos resolver esse erro de compilação relaxando um pouco o nível de acesso à propriedade, utilizando o modificador **protected**

```tsx
class View {
  protected _element: Element;

  constructor(selector: string) {
    this._element = document.querySelector(selector);
  }
}
```
