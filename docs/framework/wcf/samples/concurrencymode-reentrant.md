---
title: ConcurrencyMode Reentrant
ms.date: 03/30/2017
ms.assetid: b2046c38-53d8-4a6c-a084-d6c7091d92b1
ms.openlocfilehash: 613a1ed827173b3915892dda54dd20ebabdf6dcf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183892"
---
# <a name="concurrencymode-reentrant"></a>ConcurrencyMode Reentrant
Cet exemple illustre la nécessité d'utiliser ConcurrencyMode.Reentrant sur une implémentation de service et les conséquences d'une telle utilisation. ConcurrencyMode.Reentrant implique que le service (plus exactement l'interface de rappel) traite un seul message à la fois à un instant donné (traitement similaire à celui proposé par le mode `ConcurencyMode.Single`). Pour assurer la sécurité des threads, Windows `InstanceContext` Communication Foundation (WCF) verrouille le traitement d’un message afin qu’aucun autre message ne puisse être traité. En mode ConcurrencyMode.Reentrant, le contexte `InstanceContext` est déverrouillé juste avant que le service n'effectue un appel externe, autorisant ainsi le prochain appel (lequel peut être réentrant tel qu'illustré dans l'exemple) et l'obtention du verrouillage lorsque le service reçoit la réponse à son appel. L'exemple illustre ce comportement en montrant comment un client et un service peuvent s'envoyer des messages en utilisant un contrat duplex.  
  
 Le contrat défini correspond à un contrat duplex dans lequel la méthode `Ping` est implémentée par le service et la méthode de rappel `Pong` par le client. Le client appelle la méthode `Ping` du serveur à l'aide d'un compteur de cycles initiant par la même l'appel. Le service s'assure que la valeur du compteur de cycles n'est pas égale à zéro, puis appelle la méthode de rappel `Pong` tout en décrémentant la valeur de ce compteur. Ce processus est illustré par l'exemple de code suivant.  
  
```csharp
public void Ping(int ticks)  
{  
     Console.WriteLine("Ping: Ticks = " + ticks);  
     //Keep pinging back and forth till Ticks reaches 0.  
     if (ticks != 0)  
     {  
         OperationContext.Current.GetCallbackChannel<IPingPongCallback>().Pong((ticks - 1));  
     }  
}  
```  
  
 L'implémentation de la méthode de rappel `Pong` obéit à la même logique que l'implémentation de la méthode `Ping`. Cela signifie, en d'autres termes, que cette méthode s'assure d'abord que le nombre de cycles n'est pas égal à zéro, puis qu'elle appelle la méthode `Ping` sur le canal de rappel (dans ce cas, il s'agit du canal utilisé pour envoyer le message `Ping` d'origine) tout en décrémentant la valeur du compteur de 1. Lorsque ce nombre atteint zéro, la méthode est retournée, désencapsulant toutes les réponses au premier appel initié par le client. Ce processus est illustré dans l'implémentation du rappel.  
  
```csharp
public void Pong(int ticks)  
{  
    Console.WriteLine("Pong: Ticks = " + ticks);  
    if (ticks != 0)  
    {  
        //Retrieve the Callback  Channel (in this case the Channel which was used to send the  
        //original message) and make an outgoing call until ticks reaches 0.  
        IPingPong channel = OperationContext.Current.GetCallbackChannel<IPingPong>();  
        channel.Ping((ticks - 1));  
    }  
}  
```  
  
 Les méthodes `Ping` et `Pong` sont toutes deux du type demande-réponse, ce qui signifie que le premier appel de la méthode `Ping` est retourné uniquement une fois l'appel de `CallbackChannel<T>.Pong()` retourné. Sur le client, la méthode `Pong` ne peut pas être retournée tant que le prochain appel de la méthode `Ping` effectué n'est pas retourné. Le rappel et le service devant tous deux effectuer des appels externes de type demande-réponse avant de pouvoir répondre à la demande en attente, le comportement ConcurrencyMode.Reentrant doit être spécifié pour leurs implémentations respectives.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les échantillons de la Fondation De communication Windows.](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)  
  
2. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Pour exécuter l’échantillon dans une configuration mono-ou cross-machine, suivez les instructions dans [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="demonstrates"></a>Illustre le  
 Pour exécuter l'exemple et générer les projets de client et de serveur. Ouvrez ensuite deux fenêtres de commande \<et modifiez les répertoires pour l’échantillon \<>-CS-Service-bin-debug et échantillonnez>-CS-Client-bin-debug répertoires. Ensuite, commencez le `service.exe` service en tapant, puis invoquez le Client.exe avec la valeur initiale des tiques passées comme un argument d’entrée. Le code suivant illustre le résultat pour 10 cycles.  
  
```console  
Prompt>Service.exe  
ServiceHost Started. Press Enter to terminate service.  
Ping: Ticks = 10  
Ping: Ticks = 8  
Ping: Ticks = 6  
Ping: Ticks = 4  
Ping: Ticks = 2  
Ping: Ticks = 0  
  
Prompt>Client.exe 10  
Pong: Ticks = 9  
Pong: Ticks = 7  
Pong: Ticks = 5  
Pong: Ticks = 3  
Pong: Ticks = 1  
```  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons. Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Reentrant`  
