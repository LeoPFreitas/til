# Inferencia de tipos

Mesmo que cada local de armazenamento tenha um tipo estático no TypeScript, nem sempre é necessário especificá-lo explicitamente. O TypeScript geralmente pode inferir isso.

```tsx
// Model de negotiations
class Negotiations {
  // é do lispo array que contem objetos negotiation
  // private _negotiations: Array<Negotiation> = [];
  private _negotiations: Negotiation[] = [];

  adiciona(negotiation: Negotiation) {
    this._negotiations.push(negotiation);
  }

  toArray(): Negotiation[] {
    return this._negotiations;
  }
}

// Model Negotiation
class Negotiation {
  constructor(
    private _data: Date,
    private _quantity: number,
    private _value: number
  ) {}

  get data() {
    return this._data;
  }

  get quantity() {
    return this._quantity;
  }

  get value() {
    return this._value;
  }

  get volume() {
    return this._quantity * this._value;
  }
}

// Controller
class NegotiationController {
  private _inputData: HTMLInputElement;
  private _inputQuantity: HTMLInputElement;
  private _inputValue: HTMLInputElement;
  
  // Perceba a inferencia de tipos
  // O TS entende que _negotiations é -> (property) NegotiationController._negotiations: Negotiations private _negotiations = new Negotiations();
  constructor() {
    this._inputData = <HTMLInputElement>document.querySelector("#data");
    this._inputQuantity = <HTMLInputElement>document.querySelector("#quantity");
    this._inputValue = <HTMLInputElement>document.querySelector("#value");
  }

  adiciona(event: Event) {
    event.preventDefault();

    const negotiation = new Negotiation(
      new Date(this._inputData.value.replace(/-/g, ",")),
      parseInt(this._inputQuantity.value),
      parseFloat(this._inputValue.value)
    );

    console.log(negotiation);
  }
}
```
