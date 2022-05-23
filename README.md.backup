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

## Tasks
- Introduzido no .Net 4 para facilitar o uso e gerenciamento de threads;
- Uma Task (tarefa) recebe um trabalho a ser executado, o TaskScheduler (quem gerencia esse trabalho) determina a melhor forma de dividir o trabalho (criação de threads);
- A exemplo de uma Thread uma Task também ocorre em linhas de execução diferentes da principal, logo precisamos de uma forma para saber quando o trabalho foi concluido;
- Podemos usar o Task.WaitAll para bloquear a linha de execução principal até que todas as tasks sejam concluídas;
- Também podemos usar o Task.WhenAll, que retorna uma Task ao final da execução das anteriores, desse modo podemos executar algo novo com o ContinueWith;
- É importante destacar que, sempre que necessário manipular a interface gráfica da linha de execução inicial precisamos informar o gerenciador usado com o TaskScheduler.FromCurrentSynchronizationContext;

```
var taskSchedulerUI = TaskScheduler.FromCurrentSynchronizationContext();


var tarefas = Task.Factory.StartNew(() =>
{
    // executar uma tarefa aqui
});


Task.WhenAll(tarefas)
  .ContinueWith(task =>
  {
    // primeiro tratamento pós execução
  }, taskSchedulerUI)
  .ContinueWith(task =>
  {
    // segundo tratamento pós execução
  }, taskSchedulerUI);
```