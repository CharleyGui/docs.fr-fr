---
title: Hello World avec le service de routage
ms.date: 03/30/2017
ms.assetid: 0f4b0d5b-6522-4ad5-9f3a-baa78316d7d1
ms.openlocfilehash: ae0615c8cf2fa33f3bb363f77c0d06440b6afc13
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743710"
---
# <a name="hello-world-with-the-routing-service"></a>Hello World avec le service de routage
Cet exemple illustre le service de routage Windows Communication Foundation (WCF). Le service de routage est un composant WCF qui facilite l’inclusion d’un routeur basé sur le contenu dans votre application. Cet exemple adapte l’exemple de calculatrice WCF standard pour communiquer à l’aide du service de routage. Dans cet exemple, le client Calculator est configuré pour envoyer des messages à un point de terminaison exposé par le routeur. Le service de routage (Routing Service) est configuré de façon à accepter tous les messages qui lui sont envoyés et les transférer à un point de terminaison qui correspond au service Calculator. Les messages envoyés à partir du client sont donc reçus par le routeur et reroutés au véritable service Calculator. Les messages du service Calculator sont renvoyés au routeur, qui à son tour les retransmet au client Calculator.

### <a name="to-use-this-sample"></a>Pour utiliser cet exemple

1. À l’aide de Visual Studio 2012, ouvrez HelloRoutingService. sln.

2. Appuyez sur F5 ou CTRL+MAJ+B.

    > [!NOTE]
    > Si vous appuyez sur F5, le client Calculator démarre automatiquement. Si vous appuyez sur CTRL+MAJ+B (génération), vous devez démarrer vous-même les applications suivantes.
    >
    > 1. Client Calculator (./CalculatorClient/bin/client.exe)
    > 2. Service Calculator (./CalculatorService/bin/service.exe)
    > 3. Routing service (./RoutingService/bin/RoutingService.exe)

3. Appuyez sur ENTRÉE pour démarrer le client.

     Vous devez voir la sortie suivante :

    ```console
     Add(100,15.99) = 115.99

     Subtract(145,76.54) = 68.46

     Multiply(9,81.25) = 731.25

     Divide(22,7) = 3.14285714285714
    ```

## <a name="configurable-via-code-or-appconfig"></a>Configurable au moyen d'un code ou d'un fichier App.config
 L'exemple est fourni en étant configuré de façon à utiliser un fichier App.config pour définir le comportement du routeur. Vous pouvez également renommer le fichier App.config afin qu'il ne soit pas reconnu et supprimer les marques de commentaire de l'appel de méthode à ConfigureRouterViaCode(). Quelle que soit la méthode employée, le comportement de routeur obtenu est le même.

### <a name="scenario"></a>Scénario
 Cet exemple illustre l'utilisation du routeur en tant que pompe de messages de base. Le service de routage fait office de nœud de proxy transparent configuré pour passer les messages directement à un ensemble préconfiguré de points de terminaison de destination.

### <a name="real-world-scenario"></a>Scénario réel
 Contoso souhaite augmenter la flexibilité en matière d'affectation de noms, d'adressage, de configuration et de sécurité de ses services. Pour ce faire, la société place une pompe de messages de base devant ses services, qui fera office de point de terminaison face au public. Cela lui permet de renforcer la sécurité devant ses véritables services et de simplifier l'implémentation de solutions à montée en puissance parallèle ou du contrôle des versions du service à une date ultérieure.

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Cet exemple se trouve dans le répertoire suivant.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\HelloRoutingService`  
  
## <a name="see-also"></a>Voir aussi

- [Hébergement AppFabric et exemples de persistance](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))
