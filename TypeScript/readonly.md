# Propriedade readonly

Utilizar o modificador **readonly**  poupa ter que criar os getters e setters. 

- Se o objetivo for nao permitir que ninguem do mundo externo ao da classe possa acessar as propriedades, entao voce deve manter o private.

```tsx
// classe antes
export class Negociacao {

    constructor(private _data: Date, private _quantidade: number, private _valor: number) {}

    get data() {

        return this._data;
    }

    get quantidade() {

        return this._quantidade;
    }

    get valor() {

        return this._valor;
    }

    get volume() {

        return this._quantidade * this._valor;
    }
}

// readonly
export class Negociacao {

    constructor(readonly data: Date, readonly quantidade: number, readonly valor: number) {}

    get volume() {

        return this.quantidade * this.valor;
    }
}
```
