# Decorator throttle

Podemos criar um decorator que tem como objetivo evitar que o usuário mande varias requisicoes seguidas para o servidor.

```tsx
export function throttle(milissegundos = 500) {
  return function (
    target: any,
    propertyKey: string,
    descriptor: PropertyDescriptor
  ) {
    const originalMethod = descriptor.value;

    let timer = 0;

    descriptor.value = function (...args: any[]) {
      if (event) event.preventDefault();

      clearInterval(timer);
      timer = setTimeout(() => {
        originalMethod.apply(this, args);
      }, milissegundos);
    };

    return descriptor;
  };
}

```
