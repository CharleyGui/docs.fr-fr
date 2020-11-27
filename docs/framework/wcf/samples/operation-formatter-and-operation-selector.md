---
title: Operation Formatter and Operation Selector
ms.date: 03/30/2017
ms.assetid: 1c27e9fe-11f8-4377-8140-828207b98a0e
ms.openlocfilehash: a49b466a940b63b70509ba76e62a9b9c5a36ad61
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96260030"
---
# <a name="operation-formatter-and-operation-selector"></a>Operation Formatter and Operation Selector

Cet exemple montre comment les points d’extensibilité Windows Communication Foundation (WCF) peuvent être utilisés pour autoriser les données de message dans un format différent de celui attendu par WCF. Par défaut, les formateurs WCF attendent que les paramètres de méthode soient inclus sous l' `soap:body` élément. L'exemple montre comment implémenter à la place un formateur d'opération personnalisé qui analyse les données de paramètre d'une chaîne de requête HTTP GET chaîne et appelle des méthodes à l'aide de ces données.  
  
 L’exemple est basé sur le [prise en main](getting-started-sample.md), qui implémente le `ICalculator` contrat de service. Il montre comment les messages d'ajout, de soustraction, de multiplication et de division peuvent être modifiés pour utiliser HTTP GET pour les demandes de client à serveur et HTTP POST avec messages POX pour les réponses de serveur à client.  
  
 Pour cela, l'exemple fournit les éléments suivants :  
  
- `QueryStringFormatter`, qui implémente <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> et <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> pour le client et le serveur respectivement, et traite les données dans la chaîne de requête.  
  
- `UriOperationSelector`, qui implémente <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> sur le serveur pour effectuer la distribution des opérations en fonction du nom de l'opération dans la demande GET.  
  
- Comportement de point de terminaison `EnableHttpGetRequestsBehavior` (et configuration correspondante), qui ajoute le sélecteur d'opération nécessaire à l'exécution.  
  
- Indique comment insérer un nouveau formateur d'opération dans l'exécution.  
  
- Dans cet exemple, le client et le service sont tous deux des applications consoles (.exe).  
  
> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
## <a name="key-concepts"></a>Concepts clés  

 `QueryStringFormatter` -Le formateur d’opération est le composant de WCF qui est responsable de la conversion d’un message en un tableau d’objets de paramètres et d’un tableau d’objets de paramètre en message. Cela est effectué sur le client à l'aide de l'interface <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> et sur le serveur avec l'interface <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>. Ces interfaces permettent aux utilisateurs d'obtenir les messages de demande et de réponse des méthodes `Serialize` et `Deserialize`.  
  
 Dans cet exemple, `QueryStringFormatter` implémente ces deux interfaces et est implémenté sur le client et le serveur.  
  
 Demande :  
  
- L'exemple utilise la classe <xref:System.ComponentModel.TypeConverter> pour convertir les données de paramètre du message de demande en chaînes et vice versa. Si un <xref:System.ComponentModel.TypeConverter> n'est pas disponible pour un type spécifique, l'exemple de formateur lève une exception.  
  
- Dans la méthode `IClientMessageFormatter.SerializeRequest` sur le client, le formateur crée un URI avec l''adresse To appropriée et ajoute le nom d'opération en tant que suffixe. Ce nom est utilisé pour la distribution à l'opération appropriée sur le serveur. Il prend ensuite le tableau d'objets de paramètre et sérialise les données de paramètre dans la chaîne de requête URI à l'aide des noms de paramètre et des valeurs converties par la classe <xref:System.ComponentModel.TypeConverter>. Cette valeur est affectée aux propriétés <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> et <xref:System.ServiceModel.Channels.MessageProperties.Via%2A>, puis à cet URI. <xref:System.ServiceModel.Channels.MessageProperties> est accessible à l'aide de la propriété <xref:System.ServiceModel.Channels.Message.Properties%2A>.  
  
- Dans la méthode `IDispatchMessageFormatter.DeserializeRequest` sur le serveur, le formateur récupère l'URI `Via` dans les propriétés de message de la demande entrante. Il analyse les paires nom-valeur dans la chaîne de requête URI en fonction des noms de paramètre et des valeurs et utilise les noms de paramètre et les valeurs pour compléter le tableau de paramètres passé dans la méthode. Notez que la distribution des opérations s'est déjà produite, donc le suffixe du nom de l'opération est ignoré dans cette méthode.  
  
 Réponse :  
  
- Dans cet exemple, HTTP GET est utilisé uniquement pour la demande. Le formateur délègue l'envoi de la réponse au formateur d'origine qui aurait été utilisé pour générer un message XML. L'un des objectifs de cet exemple est de montrer comment un tel formateur déléguant peut être implémenté.  
  
### <a name="uripathsuffixoperationselector-class"></a>Classe UriPathSuffixOperationSelector  

 L'interface <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> permet aux utilisateurs d'implémenter leur propre logique pour indiquer pour quelle opération un message particulier doit être distribué.  
  
 Dans cet exemple, `UriPathSuffixOperationSelector` doit être implémenté sur le serveur pour sélectionner l'opération appropriée parce que le nom de l'opération est inclus dans l'URI HTTP GET plutôt que dans un en-tête d'action dans le message. L'exemple est configuré pour des noms d'opération non sensibles à la casse uniquement.  
  
 La méthode `SelectOperation` prend le message entrant et recherche l'URI `Via` dans ses propriétés de message. Elle extrait le suffixe du nom de l'opération de l'URI, recherche une table interne pour obtenir le nom de l'opération à laquelle le message doit être distribué, et retourne ce nom d'opération.  
  
### <a name="enablehttpgetrequestsbehavior-class"></a>Classe EnableHttpGetRequestsBehavior  

 Le composant `UriPathSuffixOperationSelector` peut être installé par programme ou par l'intermédiaire d'un comportement de point de terminaison. L'exemple implémente le comportement `EnableHttpGetRequestsBehavior`, spécifié dans le fichier de configuration de l'application du service.  
  
 Sur le serveur :  
  
 Le <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> a pour valeur l'implémentation <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector>.  
  
 Par défaut, WCF utilise un filtre d’adresse de correspondance exacte. L'URI sur le message entrant contient un suffixe de nom d'opération suivi par une chaîne de requête qui contient des données de paramètre, donc le comportement de point de terminaison modifie également le filtre d'adresse en filtre de correspondance du préfixe. Elle utilise WCF <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> à cet effet.  
  
### <a name="installing-operation-formatters"></a>Installation des formateurs d'opération  

 Les comportements d'opération qui spécifient des formateurs sont uniques. Un tel comportement est toujours implémenté par défaut pour chaque opération pour créer le formateur d'opération nécessaire. Toutefois, ces comportements ressemblent à tous les autres comportements d'opération ; ils ne sont pas identifiables par tout autre attribut. Pour installer un comportement de remplacement, l’implémentation doit rechercher des comportements de formateur spécifiques installés par le chargeur de type WCF par défaut et le remplacer ou ajouter un comportement compatible à exécuter après le comportement par défaut.  
  
 Ces comportements de formateur d'opération peuvent être installés par programme avant d'appeler <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> ou en spécifiant un comportement d'opération exécuté après le comportement par défaut. Cependant, ils ne peuvent pas être installés facilement par un comportement de point de terminaison (et par conséquent par la configuration) parce que le modèle de comportement ne permet pas à un comportement de remplacer d’autres comportements ou modifier de toute autre manière l’arborescence de description.  
  
 Sur le client :  
  
 L'implémentation <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> doit être implémentée afin qu'elle puisse convertir les demandes en demandes HTTP GET et déléguer les réponses au formateur d'origine. Cela est effectué en appelant la méthode d'assistance `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior`.  
  
 Ceci doit être fait avant d'appeler `CreateChannel`.  
  
```csharp  
void ReplaceFormatterBehavior(OperationDescription operationDescription, EndpointAddress address)  
{  
    // Remove the DataContract behavior if it is present.  
    IOperationBehavior formatterBehavior = operationDescription.Behaviors.Remove<DataContractSerializerOperationBehavior>();  
    if (formatterBehavior == null)  
    {  
        // Remove the XmlSerializer behavior if it is present.  
        formatterBehavior = operationDescription.Behaviors.Remove<XmlSerializerOperationBehavior>();  
        ...  
    }  
  
    // Remember what the innerFormatterBehavior was.  
    DelegatingFormatterBehavior delegatingFormatterBehavior = new DelegatingFormatterBehavior(address);  
    delegatingFormatterBehavior.InnerFormatterBehavior = formatterBehavior;  
   operationDescription.Behaviors.Add(delegatingFormatterBehavior);  
}  
```  
  
 Sur le serveur :  
  
- L'interface <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> doit être implémentée afin qu'elle puisse lire les demandes HTTP GET et déléguer l'écriture des réponses au formateur d'origine. Cela est effectué en appelant la même méthode d'assistance `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` que le client (consultez l'exemple de code précédent).  
  
- Ceci doit être fait avant d'appeler <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>. Dans cet exemple, nous montrons comment le formateur est modifié manuellement avant d'appeler <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>. Pour parvenir au même résultat, il est possible de dériver une classe de <xref:System.ServiceModel.ServiceHost> qui appelle `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` avant de s'ouvrir (consultez la documentation et les exemples relatifs à l'hébergement).  
  
### <a name="user-experience"></a>Expérience utilisateur  

 Sur le serveur :  
  
- L'implémentation serveur `ICalculator` n'a pas besoin d'être modifiée.  
  
- L’App.config pour le service doit utiliser une liaison POX personnalisée qui affecte à l’attribut `messageVersion` de l’élément `textMessageEncoding` la valeur `None`.  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="poxBinding">  
          <textMessageEncoding messageVersion="None" />  
          <httpTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
- L’App.config pour le service doit également spécifier le `EnableHttpGetRequestsBehavior` personnalisé en l’ajoutant à la section d’extensions de comportement et en l’utilisant.  
  
    ```xml  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="enableHttpGetRequestsBehavior">  
          <enableHttpGetRequests />  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  
    <extensions>  
      <behaviorExtensions>  
        <!-- Enabling HTTP GET requests: Behavior Extension -->  
        <add
          name="enableHttpGetRequests"           type="Microsoft.ServiceModel.Samples.EnableHttpGetRequestsBehaviorElement, QueryStringFormatter, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
      </behaviorExtensions>  
    </extensions>  
    ```  
  
- Ajoutez les formateurs d'opération avant d'appeler <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.  
  
 Sur le client :  
  
- L'implémentation cliente  n'a pas besoin d'être modifiée.  
  
- L’App.config pour le client doit utiliser une liaison POX personnalisée qui affecte à l’attribut `messageVersion` de l’élément `textMessageEncoding` la valeur `None`. À la différence du service, le client doit activer l'adressage manuel afin que l'adresse To sortante puisse être modifiée.  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="poxBinding">  
          <textMessageEncoding messageVersion="None" />  
          <httpTransport manualAddressing="True" />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
- L'App.config pour le client doit spécifier le même `EnableHttpGetRequestsBehavior` personnalisé que le serveur.  
  
- Ajoutez les formateurs d'opération avant d'appeler <xref:System.ServiceModel.ChannelFactory%601.CreateChannel>.  
  
 Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client. Les quatre opérations (addition, soustraction, multiplication et division) doivent réussir.  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Formatters\QueryStringFormatter`  
  
##### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pour générer la solution, suivez les instructions de [la création des exemples de Windows Communication Foundation](building-the-samples.md).  
  
3. Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).  
