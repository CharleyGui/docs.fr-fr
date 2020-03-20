---
title: Multiple Endpoints at a Single ListenUri
ms.date: 03/30/2017
ms.assetid: 911ffad4-4d47-4430-b7c2-79192ce6bcbd
ms.openlocfilehash: 8e26cc18ed35c446dda120c678dd7e879c756c0f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183486"
---
# <a name="multiple-endpoints-at-a-single-listenuri"></a>Multiple Endpoints at a Single ListenUri
Cet exemple présente un service qui héberge plusieurs points de terminaison au niveau d'un `ListenUri` unique. Cet échantillon est basé sur le [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) qui met en œuvre un service de calculatrice.  
  
> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 Comme le démontre l’échantillon [de plusieurs points d’end,](../../../../docs/framework/wcf/samples/multiple-endpoints.md) un service peut héberger plusieurs points de terminaison, chacun avec des adresses différentes et peut-être aussi des fixations différentes. Cet exemple montre qu'il est possible d'héberger plusieurs points de terminaison à la même adresse. Il montre également les différences entre les deux types d'adresses d'un point de terminaison : `EndpointAddress` et `ListenUri`.  
  
 `EndpointAddress` est l'adresse logique d'un service. Il s'agit de l'adresse à laquelle les messages SOAP sont adressés. `ListenUri` est l'adresse physique du service. Elle comporte les informations sur l'adresse et le port sur lesquels le point de terminaison de service écoute réellement les messages sur l'ordinateur actuel. Dans la plupart des cas, il n'est pas nécessaire que ces adresses différèrent ; lorsque `ListenUri` n'est pas spécifié de manière explicite, la valeur par défaut est l'URI de `EndpointAddress` du point de terminaison. Dans certains cas, il est utile de les distinguer, par exemple lors de la configuration d'un routeur, qui peut accepter des messages adressé à un certain nombre de services différents.  
  
## <a name="service"></a>Service  
 Le service dans cet exemple a deux contrats : `ICalculator` et `IEcho`. Outre le point de terminaison habituel `IMetadataExchange`, il existe également trois points de terminaison d'application, tel qu'indiqué dans le code suivant.  
  
```xml  
<endpoint address="urn:Stuff"  
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.ICalculator"
        listenUri="http://localhost/servicemodelsamples/service.svc" />  
<endpoint address="urn:Stuff"  
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IEcho"
        listenUri="http://localhost/servicemodelsamples/service.svc" />  
<endpoint address="urn:OtherEcho"  
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IEcho"
        listenUri="http://localhost/servicemodelsamples/service.svc" />  
```  
  
 Les trois points de terminaison sont hébergés au niveau du même `ListenUri` et utilisent le même `binding` - les mêmes points de terminaison au niveau du même `ListenUri` doivent avoir la même liaison, car ils partagent une pile de canaux unique qui écoute les messages à cette adresse physique sur l'ordinateur. L'`address` de chaque point de terminaison est une adresse URN ; bien que les adresses représentent généralement des emplacements physiques, il peut en fait s'agir de n'importe quel type d'URI, car l'adresse est utilisée à des fins de correspondance et de filtrage, tel qu'indiqué dans cet exemple.  
  
 Parce que les trois points `ListenUri`de terminaison partagent le même , quand un message arrive là, Windows Communication Foundation (WCF) doit décider quel point de terminaison le message est destiné à. Chaque point de terminaison comporte un filtre de messages composé de deux parties : le filtre d'adresse et le filtre de contrat. Le filtre d'adresse met en correspondance le `To` du message SOAP et l'adresse du point de terminaison de service. Par exemple, seuls les messages adressés `To "Urn:OtherEcho"` sont des candidats pour le troisième point de terminaison de ce service. Le filtre de contrat correspond aux actions associées aux opérations d'un contrat spécifique. Par exemple, des messages avec l'action de `IEcho`. `Echo` correspond aux filtres de contrat du deuxième et du troisième point de terminaison de ce service, car ces deux points de terminaison hébergent le contrat `IEcho`.  
  
 La combinaison du filtre d'adresse et du filtre de contrat permet donc d'acheminer chaque message qui arrive au niveau du `ListenUri` de ce service vers le point de terminaison approprié. Le troisième point de terminaison se distingue des deux autres en ce sens qu'il accepte des messages envoyés à une adresse différente des autres points de terminaison. Le premier et le deuxième point de terminaison se distinguent l'un de l'autre par leurs contrats (l'action du message entrant).  
  
## <a name="client"></a>Client  
 À l'instar des points de terminaison sur le serveur, les points de terminaison de client ont également deux adresses différentes. Sur le serveur et le client, l'adresse logique est appelée `EndpointAddress`. Mais si l'adresse physique est appelée `ListenUri` sur le serveur, elle est appelée `Via` sur le client.  
  
 Tout comme sur le serveur, ces deux adresses sont par défaut les mêmes. `Via` permet de spécifier sur le client un `ClientViaBehavior` différent de l'adresse du point de terminaison.  
  
```csharp  
Uri via = new Uri("http://localhost/ServiceModelSamples/service.svc");  
CalculatorClient calcClient = new CalculatorClient();  
calcClient.ChannelFactory.Endpoint.Behaviors.Add(  
        new ClientViaBehavior(via));  
```  
  
 Comme habituellement, l'adresse provient du fichier configuration client généré par Svcutil.exe. `Via` (qui correspond au `ListenUri` du service) n'apparaît pas dans les métadonnées du service et ces informations doivent donc être communiquées au client hors bande (à l'instar de l'adresse de métadonnées du service).  
  
 Le client dans cet exemple envoie des messages à chacun des trois points de terminaison d'application du serveur afin de montrer qu'il peut communiquer avec (et différencier) les trois, même s'ils ont tous le même `Via`.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les échantillons de la Fondation De communication Windows.](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)  
  
2. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Pour exécuter l’échantillon dans une configuration mono-ou cross-machine, suivez les instructions dans [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    > Si vous utilisez plusieurs ordinateurs, vous devez remplacer localhost dans le fichier Client.cs par le nom de l'ordinateur de service.  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons. Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleEndpointsSingleUri`  
