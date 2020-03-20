---
title: Custom Message Interceptor
ms.date: 03/30/2017
ms.assetid: 73f20972-53f8-475a-8bfe-c133bfa225b0
ms.openlocfilehash: 433b14433a7e2dd6edad551a2732e9049a9861ea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145084"
---
# <a name="custom-message-interceptor"></a>Custom Message Interceptor
Cet exemple montre l'utilisation du modèle d'extensibilité des canaux. Indique en particulier comment implémenter un élément de liaison personnalisé qui crée des fabrications de canaux et des écouteurs de canal pour intercepter tous les messages entrants et sortants à un point particulier dans la pile d’exécution. L'exemple inclut également un client et serveur qui montrent l'utilisation de ces fabrications personnalisées.  
  
 Dans cet exemple, le client et le service sont tous deux des programmes de console (.exe). Le client et le service utilisent une bibliothèque commune (.dll) qui contient l’élément de liaison personnalisé et ses objets d’exécution associés.  
  
> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons. Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\MessageInterceptor`  
  
 L’échantillon décrit la procédure recommandée pour créer un canal personnalisé en couches dans Windows Communication Foundation (WCF), en utilisant le cadre du canal et en suivant les meilleures pratiques de WCF. Les étapes de la création d'un canal superposé personnalisé sont les suivantes :  
  
1. Déterminez les formes de canal que votre fabrication et écouteur de canal prendra en charge.  
  
2. Créez une fabrication et un écouteur de canal qui prennent en charge vos formes de canal.  
  
3. Ajoutez un élément de liaison qui ajoute le canal superposé personnalisé à une pile de canaux.  
  
4. Ajoutez une section d’extension d’élément de liaison afin d’exposer le nouvel élément de liaison au système de configuration.  
  
## <a name="channel-shapes"></a>Formes de canal  
 La première étape de l'écriture d'un canal superposé personnalisé consiste à déterminer les formes requises pour le canal. Pour notre inspecteur de message, nous prenons en charge les formes qui la couche ci-dessous prend en charge (par exemple, si la couche ci-dessous peux générer <xref:System.ServiceModel.Channels.IOutputChannel> et <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, nous exposons alors également <xref:System.ServiceModel.Channels.IOutputChannel> et <xref:System.ServiceModel.Channels.IDuplexSessionChannel>).  
  
## <a name="channel-factory-and-listener-factory"></a>Fabrication de canal et d'écouteur  
 L'étape suivante de l'écriture d'un canal superposé personnalisé consiste à créer une implémentation de <xref:System.ServiceModel.Channels.IChannelFactory> pour les canaux clients et de <xref:System.ServiceModel.Channels.IChannelListener> pour les canaux de service.  
  
 Ces classes prennent une fabrication et un écouteur internes, puis leur délèguent tout les appels à l'exception de `OnCreateChannel` et `OnAcceptChannel`.  
  
```csharp
class InterceptingChannelFactory<TChannel> : ChannelFactoryBase<TChannel>  
{
    //...
}

class InterceptingChannelListener<TChannel> : ListenerFactoryBase<TChannel>  
{
    //...
}  
```  
  
## <a name="adding-a-binding-element"></a>Ajout d'un élément de liaison  
 l’exemple définit un élément de liaison personnalisé : `InterceptingBindingElement`. `InterceptingBindingElement`prend `ChannelMessageInterceptor` un comme une entrée, et l’utilise `ChannelMessageInterceptor` pour manipuler les messages qui passent à travers elle. C'est la seule classe qui doit être publique. La fabrication, l'écouteur et les canaux peuvent tous être des implémentations internes des interfaces d'exécution publiques.  
  
```csharp
public class InterceptingBindingElement : BindingElement
{
}
```  
  
## <a name="adding-configuration-support"></a>Ajout de la prise en charge de la configuration  
 Pour s'intégrer avec la configuration de liaison, la bibliothèque définit un gestionnaire de section de configuration comme section d'extension d'élément de liaison. Les fichiers de configuration du client et du serveur doivent enregistrer l'extension d'élément de liaison avec le système de configuration. Les implémenteurs qui souhaitent exposer leur élément de liaison au système de configuration peuvent dériver de cette classe.  
  
```csharp
public abstract class InterceptingElement : BindingElementExtensionElement
{
    //...
}
```  
  
## <a name="adding-policy"></a>Ajout d'une stratégie  
 Pour s'intégrer avec notre système de stratégie, `InterceptingBindingElement` implémente IPolicyExportExtension pour signaler que nous devons participer à la génération de la stratégie. Pour prendre en charge l'importation de la stratégie sur un client généré, l'utilisateur peut enregistrer une classe dérivée de `InterceptingBindingElementImporter` et substituer `CreateMessageInterceptor`() pour générer leur classe `ChannelMessageInterceptor` activée par stratégie.  
  
## <a name="example-droppable-message-inspector"></a>Exemple : Inspecteur de message pouvant être déposé  
 L'exemple comporte un exemple d'implémentation de `ChannelMessageInspector` qui supprime des messages.  
  
```csharp
class DroppingServerElement : InterceptingElement  
{  
    protected override ChannelMessageInterceptor CreateMessageInterceptor()  
    {  
        return new DroppingServerInterceptor();  
    }  
}  
```  
  
 Vous pouvez y accéder à partir de la configuration comme suit :  
  
```xml  
<configuration>  
    ...  
    <system.serviceModel>  
        ...  
        <extensions>  
            <bindingElementExtensions>  
                <add name="droppingInterceptor"
                   type=  
          "Microsoft.ServiceModel.Samples.DroppingServerElement, library"/>  
            </bindingElementExtensions>  
        </extensions>  
    </system.serviceModel>  
</configuration>  
```  
  
 Le client et le serveur utilisent cette section de configuration récemment créée afin dans d'insérer les fabrications personnalisées au niveau le plus bas de leurs piles d'exécution de canaux (au-dessus du niveau du transport).  
  
```xml  
<customBinding>  
  <binding name="sampleBinding">  
    <droppingInterceptor/>  
    <httpTransport/>  
  </binding>  
</customBinding>  
```  
  
 Le client utilise la bibliothèque `MessageInterceptor` pour ajouter un en-tête personnalisé aux messages portant un numéro pair. Le service utilise en revanche la bibliothèque `MessageInterceptor` pour supprimer les messages qui n'ont pas cet en-tête spécifique.  
  
 La sortie du client suivante doit s'afficher après avoir exécuté le service puis le client.  
  
```console  
Reporting the next 10 wind speed  
100 kph  
Server dropped a message.  
90 kph  
80 kph  
Server dropped a message.  
70 kph  
60 kph  
Server dropped a message.  
50 kph  
40 kph  
Server dropped a message.  
30 kph  
20 kph  
Server dropped a message.  
10 kph  
Press ENTER to shut down client  
```  
  
 Le client signale 10 vitesses de vent différentes au service, mais n’en référence que la moitié avec l’en-tête spécifique.  
  
 La sortie suivante doit s'afficher sur le service :  
  
```console  
Press ENTER to exit.  
Dangerous wind detected! Reported speed (90) is greater than 64 kph.  
Dangerous wind detected! Reported speed (70) is greater than 64 kph.  
5 wind speed reports have been received.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Installez ASP.NET 4.0 à l’aide de la commande suivante.  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les échantillons de la Fondation De communication Windows.](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)  
  
3. Pour construire la solution, suivez les instructions dans [la construction des échantillons de la Fondation De communication Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Pour exécuter l’échantillon dans une configuration mono-ou cross-machine, suivez les instructions dans [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
5. Exécutez d'abord Service.exe, puis Client.exe. Examinez ensuite la sortie dans les deux fenêtres de console.  
