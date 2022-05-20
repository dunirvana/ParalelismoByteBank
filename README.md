# Alura-Paralelismo-com-CSharp-e-.NET
Progresso de nosso desenvolvimento no curso de Paralelismo com C# e .NET

## Thread
- Thread é uma linha de execução, a execução de uma aplicação por si só é uma Thread;
- Podemos criar outras Threads e desse modo realizar o processamento de forma paralela, no C# temos uma objeto com o mesmo nome;
- Quando criada a Thread recebe um delegate, o método que deve ser executado;
- Para que a execução ocorra devemos iniciar a mesma (Start);
- É possível verificar se ela ainda esta em execução (IsAlive);

```
Thread thread1 = new Thread(() =>
{
	// executar uma tarefa aqui
});

while (thread1.IsAlive)
{
    // o loop só encerra quando a thread encerrar seu trabalho
}
```