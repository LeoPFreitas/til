# Tipo never

O TypeScript possui o tipo never → aplocável a métodos ou funções que por algum motivo, planejado ou não, podem não terminar sua execução de seu bloco.

Exemplos clássicos são os de métodos que caem em um loop infinito ou de métodos que sempre retornam exceções. Exceções fazem com que o método não execute até o fim.

Geralmente não usamos esse tipo em nosso código, mas ele pode aparecer como aviso do compilador. Quando aparecer, você já saberá que a execução do seu método nunca chegará até o fim, sendo um forte indicativo de um bug em seu código.

**OBS:**

- never ≠ void
