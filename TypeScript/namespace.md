# Namespace nas Views

É possível criar um namespace para as Views, Controllers, Models... Assim, o desenvolvedor pode aproveitar do autocomplete e ver facilmente quais sao as Views disponveis.

```tsx
namespace Views {
  export class MessageView extends View<string> {
    template(model: string): string {
      return `<p class='alert alert-info'>${model}</p>`;
    }
  }
}

// Temos acesso ao autocomplete
// Views.
```
