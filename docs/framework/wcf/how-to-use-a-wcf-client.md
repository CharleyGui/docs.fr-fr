---
title: 'Tutorial: Utilisez un client de la Fondation De communication Windows'
ms.date: 03/19/2019
helpviewer_keywords:
- WCF clients [WCF], using
dev_langs:
- CSharp
- VB
ms.assetid: 190349fc-0573-49c7-bb85-8e316df7f31f
ms.openlocfilehash: d2357c134aef8da204dcdb19d6c1fc93cfdc068c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184013"
---
# <a name="tutorial-use-a-windows-communication-foundation-client"></a>Tutorial: Utilisez un client de la Fondation De communication Windows

Ce tutoriel décrit la dernière des cinq tâches requises pour créer une application de base de la Windows Communication Foundation (WCF). Pour un aperçu des tutoriels, voir [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).

Une fois que vous avez créé et configuré un proxy de la Windows Communication Foundation (WCF), vous créez une instance client et compilez l’application client. Vous l’utilisez ensuite pour communiquer avec le service WCF.

Dans ce tutoriel, vous allez apprendre à :
> [!div class="checklist"]
>
> - Ajoutez du code pour utiliser le client WCF.
> - Testez le client WCF.

## <a name="add-code-to-use-the-wcf-client"></a>Ajouter du code pour utiliser le client WCF

Le code client fait les étapes suivantes :

- Instantanéise le client WCF.
- Appelle les opérations de service à partir du proxy généré.
- Ferme le client une fois l’appel d’opération terminé.

Ouvrez le fichier **Program.cs** ou **Module1.vb** du projet **GettingStartedClient** et remplacez son code par le code suivant :

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GettingStartedClient.ServiceReference1;

namespace GettingStartedClient
{
    class Program
    {
        static void Main(string[] args)
        {
            //Step 1: Create an instance of the WCF proxy.
            CalculatorClient client = new CalculatorClient();

            // Step 2: Call the service operations.
            // Call the Add service operation.
            double value1 = 100.00D;
            double value2 = 15.99D;
            double result = client.Add(value1, value2);
            Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);

            // Call the Subtract service operation.
            value1 = 145.00D;
            value2 = 76.54D;
            result = client.Subtract(value1, value2);
            Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);

            // Call the Multiply service operation.
            value1 = 9.00D;
            value2 = 81.25D;
            result = client.Multiply(value1, value2);
            Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);

            // Call the Divide service operation.
            value1 = 22.00D;
            value2 = 7.00D;
            result = client.Divide(value1, value2);
            Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);

            // Step 3: Close the client to gracefully close the connection and clean up resources.
            Console.WriteLine("\nPress <Enter> to terminate the client.");
            Console.ReadLine();
            client.Close();
        }
    }
}
```

```vb
Imports System.Collections.Generic
Imports System.Text
Imports System.ServiceModel
Imports GettingStartedClient.ServiceReference1

Module Module1

    Sub Main()
        ' Step 1: Create an instance of the WCF proxy.
        Dim Client As New CalculatorClient()

        ' Step 2: Call the service operations.
        ' Call the Add service operation.
        Dim value1 As Double = 100D
        Dim value2 As Double = 15.99D
        Dim result As Double = Client.Add(value1, value2)
        Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result)

        ' Call the Subtract service operation.
        value1 = 145D
        value2 = 76.54D
        result = Client.Subtract(value1, value2)
        Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result)

        ' Call the Multiply service operation.
        value1 = 9D
        value2 = 81.25D
        result = Client.Multiply(value1, value2)
        Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result)

        ' Call the Divide service operation.
        value1 = 22D
        value2 = 7D
        result = Client.Divide(value1, value2)
        Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result)

        ' Step 3: Close the client to gracefully close the connection and clean up resources.
        Console.WriteLine()
        Console.WriteLine("Press <Enter> to terminate the client.")
        Console.ReadLine()
        Client.Close()

    End Sub

End Module
```

Notez `using` l’énoncé (pour `Imports` le visuel CMD) `GettingStartedClient.ServiceReference1`ou (pour Visual Basic) qui importe . Cette déclaration importe le code généré par Visual Studio avec la fonction **Add Service Reference.** Le code instantanéise le proxy WCF et appelle chacune des opérations de service que le service de calculatrice expose. Il ferme ensuite le proxy et met fin au programme.

## <a name="test-the-wcf-client"></a>Testez le client WCF

### <a name="test-the-application-from-visual-studio"></a>Testez l’application de Visual Studio

1. Enregistrez et générez la solution.

2. Sélectionnez le dossier **GettingStartedLib,** puis sélectionnez **Set comme startup Project** à partir du menu raccourci.

3. De **Startup Projects**, **sélectionnez GettingStartedLib** de la liste d’abandon, puis sélectionnez **Run** ou appuyez sur **F5**.

### <a name="test-the-application-from-a-command-prompt"></a>Testez l’application à partir d’une invite de commande

1. Ouvrez une invite de commande en tant qu’administrateur, puis naviguez vers votre répertoire de solution Visual Studio.

2. Pour commencer le service: Entrez *GettingStartedHost-bin-debug-GettingStartedHost.exe*.

3. Pour démarrer le client : Ouvrez une autre invite de commande, naviguez vers votre répertoire de solutions Visual Studio, puis entrez *GettingStartedClient-bin-debug-GettingStartedClient.exe*.

   *GettingStartedHost.exe* produit la sortie suivante :

   ```text
   The service is ready.
   Press <Enter> to terminate the service.

   Received Add(100,15.99)
   Return: 115.99
   Received Subtract(145,76.54)
   Return: 68.46
   Received Multiply(9,81.25)
   Return: 731.25
   Received Divide(22,7)
   Return: 3.14285714285714
   ```

   *GettingStartedClient.exe* produit la sortie suivante :

   ```text
   Add(100,15.99) = 115.99
   Subtract(145,76.54) = 68.46
   Multiply(9,81.25) = 731.25
   Divide(22,7) = 3.14285714285714

   Press <Enter> to terminate the client.
   ```

## <a name="next-steps"></a>Étapes suivantes

Vous avez maintenant terminé toutes les tâches dans le tutoriel WCF commencer. Dans ce didacticiel, vous avez appris à :

Dans ce tutoriel, vous allez apprendre à :
> [!div class="checklist"]
>
> - Ajoutez du code pour utiliser le client WCF.
> - Testez le client WCF.

Si vous avez des problèmes ou des erreurs dans l’une des étapes, suivez les étapes de l’article de dépannage pour les corriger.

> [!div class="nextstepaction"]
> [Dépannage de la Get a commencé avec des tutoriels WCF](troubleshooting-the-getting-started-tutorial.md)
