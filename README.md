# Construindo-um-Sistema-de-Hospedagem-de-um-Hotel-no-C-
Como construir um sistema de hospedagem para um hotel em C#. Aqui estão os passos que podemos seguir para criar esse projeto:

1. **Defina as classes**:
   Comece criando as classes necessárias para o seu sistema de hospedagem. Foram mencionado três classes: `Pessoa`, `Suíte` e `Reserva`. Vamos criar essas classes:

   ```csharp
   class Pessoa
   {
       public string Nome { get; set; }
       // Outras propriedades relevantes para o hóspede
   }

   class Suíte
   {
       public int Número { get; set; }
       public decimal ValorDiária { get; set; }
       // Outras propriedades relevantes para a suíte
   }

   class Reserva
   {
       public Pessoa Hóspede { get; set; }
       public Suíte SuíteReservada { get; set; }
       public DateTime DataEntrada { get; set; }
       public DateTime DataSaída { get; set; }

       public int QuantidadeHóspedes()
       {
           // Implemente a lógica para calcular a quantidade de hóspedes
           // com base nos dados da reserva
       }

       public decimal ValorTotal()
       {
           // Implemente a lógica para calcular o valor total da reserva
           // considerando a quantidade de dias e o desconto
       }
   }
   ```

2. **Implemente a lógica de cálculo da quantidade de hóspedes**:
   No método `QuantidadeHóspedes()`, podemos calcular a quantidade de hóspedes com base nos dados da reserva (por exemplo, número de adultos e crianças).

3. **Implemente a lógica de cálculo do valor total da reserva**:
   No método `ValorTotal()`, podemos calcular o valor total da reserva com base na quantidade de dias que o hóspede ficará hospedado na suíte. Lembrando de aplicar o desconto de 10% se a reserva for para mais de 10 dias.

4. **Teste o seu sistema**:
   Crie um programa principal (método `Main`) para testar todas as funcionalidades do seu sistema. Crie uma instância de `Pessoa`, uma instância de `Suíte`, faça uma reserva e exiba o valor total.

5. **Utilize uma IDE**:
   Use uma ferramenta de desenvolvimento integrado (IDE) como o Visual Studio ou o Visual Studio Code para escrever e executar o seu código.

Lembre-se de seguir as boas práticas de programação, como dividir o código em classes, usar comentários para explicar a lógica e testar cada funcionalidade separadamente.

Para calcular o valor da diária com desconto, você pode seguir os seguintes passos:

1. **Obtenha o valor da diária**:
   Primeiro, você precisa ter o valor da diária da suíte. Isso pode ser definido na classe `Suíte` como uma propriedade chamada `ValorDiária`.

2. **Calcule o número de dias da reserva**:
   Com base nas datas de entrada e saída da reserva (que você registrou na classe `Reserva`), calcule o número de dias que o hóspede ficará hospedado. Você pode usar a classe `DateTime` do C# para fazer essa conta.

3. **Aplicação do desconto**:
   Se o número de dias for maior que 10, aplique um desconto de 10% no valor total da diária. Caso contrário, o valor total será igual ao valor da diária sem desconto.

4. **Fórmula para calcular o valor total**:
   O valor total da reserva pode ser calculado da seguinte forma:
   ```
   ValorTotal = ValorDiária * NúmeroDeDias
   ```
   Se o número de dias for maior que 10, aplique o desconto:
   ```
   ValorTotalComDesconto = ValorTotal * 0.9
   ```

5. **Exemplo de implementação**:
   Aqui está um exemplo de como você pode implementar o cálculo do valor total com desconto na classe `Reserva`:

   ```csharp
   class Reserva
   {
       // ...

       public decimal ValorTotal()
       {
           int númeroDeDias = (int)(DataSaída - DataEntrada).TotalDays;
           decimal valorTotal = SuíteReservada.ValorDiária * númeroDeDias;

           if (númeroDeDias > 10)
           {
               decimal valorTotalComDesconto = valorTotal * 0.9;
               return valorTotalComDesconto;
           }

           return valorTotal;
       }
   }
   ```

Sempre lembrando de adaptar esses passos ao projeto específico e de testar o sistema para garantir que o cálculo esteja correto.

https://github.com/digitalinnovationone/trilha-net-explorando-desafio
