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

## Async / await
- Introduzido na versão 5 do C# para facilitar o trabalho com tasks;
- Ele abstrai a necessidade de conversão de tasks e resolve a questão de contexto de execução das tasks;
- O async é usado para identificar que um método esta trabalhando de forma assíncrona;
- O await aguarda a finalização da execução de uma tarefa, tornando desnecessário a intervenção manual para aguardar o término das execuções, encadeamento de novas execuções e a preocupação com o contexto das threads;
- Em resumo ele aguarda sem bloquear;

```
private async Task<string[]> MeuMetodo()
{
	var tarefas = Task.Factory.StartNew(() =>
	{
	    // executar uma tarefa aqui
	});
	
    return await Task.WhenAll(tarefas);
}

private async void MeuBtn_Click(object sender, RoutedEventArgs e)
{
    MeuBtn.IsEnabled = false;

    var resultado = await MeuMetodo();

    MeuBtn.IsEnabled = true;
}

```