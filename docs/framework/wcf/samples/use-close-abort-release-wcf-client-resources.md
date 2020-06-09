---
title: Utiliser la fermeture et l’abandon pour libérer des ressources de client WCF
description: La méthode dispose peut échouer et lever des exceptions en cas de défaillance du réseau. Cela peut provoquer un comportement indésirable. Utilisez plutôt Close et Abort pour libérer des ressources client lorsque le réseau a échoué.
ms.date: 11/12/2018
ms.assetid: aff82a8d-933d-4bdc-b0c2-c2f7527204fb
ms.openlocfilehash: b338b760f461d7b773f43dd1f5e6dbce98f9e15a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599917"
---
# <a name="close-and-abort-release-resources-safely-when-network-connections-have-dropped"></a>Fermez et abandonnez les ressources Release en toute sécurité lorsque les connexions réseau ont été supprimées

Cet exemple illustre l’utilisation `Close` des `Abort` méthodes et pour nettoyer les ressources lors de l’utilisation d’un client typé. L' `using` instruction provoque des exceptions lorsque la connexion réseau n’est pas fiable. Cet exemple est basé sur le [prise en main](getting-started-sample.md) qui implémente un service de calculatrice. Dans cet exemple, le client est une application console (.exe) et le service est hébergé par les services IIS (Internet Information Services).

> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.

Cet exemple contient deux des problèmes fréquents susceptibles de survenir lorsque l'instruction « using » C# est utilisée avec les clients typés ainsi que le code permettant de procéder au nettoyage adéquat après la survenue d'exceptions.

L'instruction « using » C# provoque l'appel de `Dispose`(). Cette méthode est identique à la méthode `Close`(), laquelle peut lever des exceptions lorsqu'une erreur réseau se produit. L'appel de `Dispose`() se produit de manière implicite au niveau de l'accolade fermante du bloc « using », cette source d'exceptions a peu de chance d'être remarquée par une personne lisant le code ou par la personne chargée de le rédiger. Cela représente une source potentielle d'erreurs d'application.

Le premier problème, illustré dans la méthode `DemonstrateProblemUsingCanThrow`, réside dans le fait que l'accolade fermante lève une exception et que le code figurant après cette accolade ne s'exécute pas :

```csharp
using (CalculatorClient client = new CalculatorClient())
{
    ...
} // <-- this line might throw
Console.WriteLine("Hope this code wasn't important, because it might not happen.");
```

Même si rien à l'intérieur du bloc « using » ne provoque la levée d'une exception ou si toutes les exceptions à l'intérieur de ce bloc sont interceptées, le code `Console.WriteLine` peut ne pas s'exécuter, l'appel implicite de `Dispose`() risquant de lever une exception.

Le second problème, illustré dans la méthode `DemonstrateProblemUsingCanThrowAndMask`, est une autre conséquence du problème résultant de la levée d'une exception par l'accolade fermante :

```csharp
using (CalculatorClient client = new CalculatorClient())
{
    ...
    throw new ApplicationException("Hope this exception was not important, because "+
                                   "it might be masked by the Close exception.");
} // <-- this line might throw an exception.
```

La méthode `Dispose`() survenant à l'intérieur d'un bloc « finally », l'exception `ApplicationException` ne sera pas visible en dehors du bloc « using » si la méthode `Dispose`() échoue. Si le code externe doit savoir à quel moment l'exception `ApplicationException` survient, le bloc « using » risque de poser un problème, car il masque cette exception.

Enfin, cette exemple illustre comment procéder à un nettoyage adéquat lors de la survenue d'exceptions dans `DemonstrateCleanupWithExceptions`. Pour ce faire, un bloc essai/interception est utilisé pour signaler les erreurs et appeler la méthode `Abort`. Pour plus d’informations sur l’interception des exceptions à partir d’appels clients, consultez l’exemple [exceptions attendues](expected-exceptions.md) .

```csharp
try
{
    ...
    client.Close();
}
catch (CommunicationException e)
{
    ...
    client.Abort();
}
catch (TimeoutException e)
{
    ...
    client.Abort();
}
catch (Exception e)
{
    ...
    client.Abort();
    throw;
}
```

> [!NOTE]
> Instruction « using » et ServiceHost : de nombreuses applications d'auto-hébergement ne se contentent pas seulement d'héberger des services et l'appel de la méthode ServiceHost.Close lève rarement une exception. Par conséquent, ces applications peuvent utiliser l'instruction « using » avec ServiceHost. Toutefois, n'oubliez pas que l'appel de la méthode ServiceHost.Close peut lever une exception `CommunicationException`. Par conséquent, si votre application continue à s'exécuter après la fermeture de ServiceHost, vous devez éviter d'utiliser l'instruction « using » et vous conformer au modèle mentionné précédemment.

Lorsque vous exécutez l'exemple, les exceptions et réponses d'opération s'affichent dans la fenêtre de console du client.

Le processus du client exécute trois scénarios qui essaient tous d'appeler `Divide`. Le premier scénario contient le code ignoré à cause de l'exception levée par la méthode `Dispose`(). Le deuxième scénario contient une exception importante masquée à cause de l'exception levée par la méthode `Dispose`(). Le troisième scénario illustre le processus de nettoyage adéquat.

Le processus client est censé donner le résultat suivant :

```console
=
= Demonstrating problem:  closing brace of using statement can throw.
=
Got System.ServiceModel.CommunicationException from Divide.
Got System.ServiceModel.Security.MessageSecurityException
=
= Demonstrating problem:  closing brace of using statement can mask other Exceptions.
=
Got System.ServiceModel.CommunicationException from Divide.
Got System.ServiceModel.Security.MessageSecurityException
=
= Demonstrating cleanup with Exceptions.
=
Calling client.Add(0.0, 0.0);
        client.Add(0.0, 0.0); returned 0
Calling client.Divide(0.0, 0.0);
Got System.ServiceModel.CommunicationException from Divide.

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple

1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

2. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).

3. Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\UsingUsing`
