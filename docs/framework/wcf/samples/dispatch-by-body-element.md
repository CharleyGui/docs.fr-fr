---
title: Dispatch by Body Element
ms.date: 03/30/2017
ms.assetid: f64a3c04-62b4-47b2-91d9-747a3af1659f
ms.openlocfilehash: 754151f856dfe09b8fd12912ab06d1d8720be016
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183709"
---
# <a name="dispatch-by-body-element"></a>Dispatch by Body Element
Cet exemple montre comment implémenter un autre algorithme pour l'assignation des messages entrants aux opérations.  
  
 Par défaut, le répartiteur modèle de service sélectionne la méthode de gestion appropriée pour un message entrant en fonction de l'en-tête d'action WS-Addressing du message ou de l'information équivalente dans la requête HTTP SOAP.  
  
 Quelques piles de services Web SOAP 1.1 qui ne suivent pas les indications du profil WS-I Basic Profile 1.1 ne distribuent pas les messages en fonction de l'URI d'action, mais plutôt selon le nom qualifié XML du premier élément contenu dans le corps SOAP. De même, le côté client de ces piles peut envoyer des messages avec un en-tête HTTP SoapAction vide ou arbitraire ayant été autorisé par la spécification SOAP 1.1.  
  
 Pour modifier le mode de distribution des messages aux méthodes, l'exemple implémente l'interface d'extensibilité <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> sur le `DispatchByBodyElementOperationSelector`. Cette classe sélectionne des opérations en fonction du premier élément du corps du message.  
  
 Le constructeur de classe attend un dictionnaire rempli avec les paires de `XmlQualifiedName` et les chaînes, dans lequel les noms qualifiés indiquent le nom du premier enfant du corps SOAP et les chaînes indiquent le nom d'opération correspondant. `defaultOperationName` est le nom de l'opération qui reçoit tous les messages qui ne peuvent pas être comparés à ce dictionnaire:  
  
```csharp
class DispatchByBodyElementOperationSelector : IDispatchOperationSelector  
{  
    Dictionary<XmlQualifiedName, string> dispatchDictionary;  
    string defaultOperationName;  
  
    public DispatchByBodyElementOperationSelector(Dictionary<XmlQualifiedName,string> dispatchDictionary, string defaultOperationName)  
    {  
        this.dispatchDictionary = dispatchDictionary;  
        this.defaultOperationName = defaultOperationName;  
    }  
}
```  
  
 Les implémentations d'<xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> sont très simples à générer puisqu'une seule méthode est présente sur l'interface : <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A>. Le rôle de cette méthode consiste à inspecter un message entrant et à retourner une chaîne égale au nom d'une méthode sur le contrat de service pour le point de terminaison actuel.  
  
 Dans cet exemple, le sélecteur d'opération acquiert une classe <xref:System.Xml.XmlDictionaryReader> pour le corps du message entrant à l'aide de <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>. Cette méthode positionne déjà le lecteur sur le premier enfant du corps du message afin que ce soit suffisant pour obtenir le nom de l'élément actuel et l'URI d'espace de noms, et les mixer dans un `XmlQualifiedName` utilisé ensuite pour voir l'opération correspondante du dictionnaire tenu par le sélecteur d'opération.  
  
```csharp
public string SelectOperation(ref System.ServiceModel.Channels.Message message)  
{  
    XmlDictionaryReader bodyReader = message.GetReaderAtBodyContents();  
    XmlQualifiedName lookupQName = new  
       XmlQualifiedName(bodyReader.LocalName, bodyReader.NamespaceURI);  
    message = CreateMessageCopy(message,bodyReader);  
    if (dispatchDictionary.ContainsKey(lookupQName))  
    {  
         return dispatchDictionary[lookupQName];  
    }  
    else  
    {  
        return defaultOperationName;  
    }  
}  
```  
  
 L'accès au corps du message avec <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> ou l'une des autres méthodes qui fournissent l'accès au contenu de corps du message entraîne le marquage du message comme lu, ce qui signifie que ce dernier n'est pas valide pour tout traitement ultérieur. Par conséquent, le sélecteur d'opération crée une copie du message entrant avec la méthode affichée dans le code suivant. Parce que la position du lecteur n'a pas été modifiée au cours de l'inspection, elle peut être référencée par le message nouvellement créé et dans lequel les propriétés et en-têtes de message sont également copiés, ce qui génère un clone exact du message d'origine :  
  
```csharp
private Message CreateMessageCopy(Message message,
                                     XmlDictionaryReader body)  
{  
    Message copy = Message.CreateMessage(message.Version,message.Headers.Action,body);  
    copy.Headers.CopyHeaderFrom(message,0);  
    copy.Properties.CopyProperties(message.Properties);  
    return copy;  
}  
```  
  
## <a name="adding-an-operation-selector-to-a-service"></a>Ajout d'un sélecteur d'opération à un service  
 Les sélecteurs d’opérations de répartition des services sont des extensions au répartiteur de la Windows Communication Foundation (WCF). Pour la sélection des méthodes sur le canal de rappel de contrats duplex, il existe également des sélecteurs d'opération clients qui fonctionnent de manière semblable aux sélecteurs d'opération de distribution décrits ici, mais ne sont pas traités de manière explicite dans cet exemple.  
  
 Comme la plupart des extensions de modèle de service, les sélecteurs d’opération de distribution sont ajoutés au répartiteur à l’aide de comportements. Un *comportement* est un objet de configuration, qui ajoute une ou plusieurs extensions au temps d’exécution de l’expédition (ou au temps d’exécution du client) ou modifie autrement ses paramètres.  
  
 Parce que les sélecteurs d'opération disposent d'une étendue de contrat, <xref:System.ServiceModel.Description.IContractBehavior> est le comportement approprié à implémenter ici. Étant donné que l'interface est implémentée sur une classe dérivée <xref:System.Attribute> comme indiqué dans le code suivant, le comportement peut être ajouté de façon déclarative à tout contrat de service. Chaque fois qu’une classe <xref:System.ServiceModel.ServiceHost> est ouverte et que l’exécution du répartiteur est générée, tous les comportements recherchés, soit en tant qu’attributs sur les contrats, opérations et implémentations de service, soit en tant qu’élément dans la configuration du service, sont automatiquement ajoutés et doivent ensuite fournir des extensions ou modifier la configuration par défaut.  
  
 Pour des raisons de concision, l'extrait de code suivant affiche seulement l'implémentation de la méthode <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> qui effectue les modifications de configuration du répartiteur dans cet exemple. Les autres méthodes ne sont pas indiquées car elles sont retournées à l'appelant sans effectuer aucun travail.  
  
```csharp
[AttributeUsage(AttributeTargets.Class|AttributeTargets.Interface)]  
class DispatchByBodyElementBehaviorAttribute : Attribute, IContractBehavior  
{  
    // public void AddBindingParameters(...)
    // public void ApplyClientBehavior(...)  
    // public void Validate(...)  
```  
  
 En premier lieu, l'implémentation <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> installe le dictionnaire de recherche pour le sélecteur d'opération en itérant sur les éléments <xref:System.ServiceModel.Description.OperationDescription> dans la classe <xref:System.ServiceModel.Description.ContractDescription> du point de terminaison de service. Ensuite, la présence du comportement `DispatchBodyElementAttribute` (une implémentation de <xref:System.ServiceModel.Description.IOperationBehavior> qui est également défini dans cet exemple) est vérifiée dans chaque description d'opération. Bien que cette classe constitue également un comportement, elle est passive et ne fournit pas de manière active de modifications de configuration apportées à l'exécution du répartiteur. Toutes ses méthodes sont retournées à l'appelant sans aucune action. Le comportement d'opération existe seulement afin que les métadonnées requises pour le nouveau mécanisme de distribution, à savoir le nom qualifié de l'élément de corps sur lequel une opération est sélectionnée, puissent être associées aux opérations respectives.  
  
 Si ce comportement est trouvé, une paire valeur créée à partir du nom qualifié XML (propriété `QName`) et le nom d'opération (propriété `Name`) sont ajoutés au dictionnaire.  
  
 Une fois le dictionnaire rempli, un nouveau `DispatchByBodyElementOperationSelector` est généré avec ces informations et défini comme le sélecteur d'opération de l'exécution du répartiteur :  
  
```csharp
public void ApplyDispatchBehavior(ContractDescription contractDescription, ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.DispatchRuntime dispatchRuntime)  
{  
    Dictionary<XmlQualifiedName,string> dispatchDictionary =
                     new Dictionary<XmlQualifiedName,string>();  
    foreach( OperationDescription operationDescription in
                              contractDescription.Operations )  
    {  
        DispatchBodyElementAttribute dispatchBodyElement =
   operationDescription.Behaviors.Find<DispatchBodyElementAttribute>();  
        if ( dispatchBodyElement != null )  
        {  
             dispatchDictionary.Add(dispatchBodyElement.QName,
                              operationDescription.Name);  
        }  
    }  
    dispatchRuntime.OperationSelector =
            new DispatchByBodyElementOperationSelector(  
               dispatchDictionary,
               dispatchRuntime.UnhandledDispatchOperation.Name);  
    }  
}  
```  
  
## <a name="implementing-the-service"></a>Implémentation du service  
 Le comportement implémenté dans cet exemple affecte directement la façon dont les messages provenant du câble sont interprétés et distribués, ce qui constitue une fonction du contrat de service. Par conséquent, le comportement doit être déclaré sur le niveau de contrat de service dans toute implémentation de service qui choisit de l'utiliser.  
  
 Le service de `DispatchByBodyElementBehaviorAttribute` projet d’échantillon applique le comportement du `OperationForBodyA()` `OperationForBodyB()` contrat `DispatchBodyElementAttribute` au `IDispatchedByBody` contrat de service et étiquette chacune des deux opérations et avec un comportement d’opération. Lorsqu'un hôte est ouvert pour un service qui implémente ce contrat, ces métadonnées sont choisies par le générateur de répartiteurs comme décrit précédemment.  
  
 Étant donné que le sélecteur d'opération effectue la distribution uniquement en fonction l'élément de corps du message et ignore l'en-tête Action, il doit indiquer au runtime de ne pas vérifier cet en-tête sur les réponses retournées en assignant le caractère générique « * » à la propriété `ReplyAction` de la classe <xref:System.ServiceModel.OperationContractAttribute>. En outre, il est nécessaire d’avoir une opération par défaut\*qui a la propriété "Action" réglé à la wildcard ". L'opération par défaut reçoit tous les messages qui ne peuvent pas être distribués et n'ont pas de `DispatchBodyElementAttribute` :  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples"),  
                            DispatchByBodyElementBehavior]  
public interface IDispatchedByBody  
{  
    [OperationContract(ReplyAction="*"),
     DispatchBodyElement("bodyA","http://tempuri.org")]  
    Message OperationForBodyA(Message msg);  
    [OperationContract(ReplyAction = "*"),
     DispatchBodyElement("bodyB", "http://tempuri.org")]  
    Message OperationForBodyB(Message msg);  
    [OperationContract(Action="*", ReplyAction="*")]  
    Message DefaultOperation(Message msg);  
}  
```  
  
 L'implémentation du service exemple est simple. Chaque méthode insère le message reçu dans un message de réponse et le retourne au client.  
  
## <a name="running-and-building-the-sample"></a>Génération et exécution de l'exemple  
 Lorsque vous exécutez l'exemple, le contenu du corps des réponses d'opération est affiché dans la fenêtre de la console cliente semblable à la sortie suivante (mis en forme).  
  
 Le client envoie trois messages au service dont l'élément du contenu du corps est nommé `bodyA`, `bodyB` et `bodyX`, respectivement. Comme il peut être différé de la description précédente et du contrat de service indiqué, le message entrant avec l'élément `bodyA` est distribué à la méthode `OperationForBodyA()`. Étant donné qu'il n'y a aucune cible de distribution explicite pour le message avec l'élément de corps `bodyX`, le message est distribué à `DefaultOperation()`. Chacune des opérations de service englobe le corps du message reçu dans un élément spécifique à la méthode et le renvoie, ce qui permet de faire correspondre clairement les messages d'entrée et de sortie pour cet exemple :  
  
```xml  
<?xml version="1.0" encoding="IBM437"?>  
<replyBodyA xmlns="http://tempuri.org">  
   <q:bodyA xmlns:q="http://tempuri.org">test</q:bodyA>  
</replyBodyA>  
<?xml version="1.0" encoding="IBM437"?>  
<replyBodyB xmlns="http://tempuri.org">  
  <q:bodyB xmlns:q="http://tempuri.org">test</q:bodyB>  
</replyBodyB>  
<?xml version="1.0" encoding="IBM437"?>  
<replyDefault xmlns="http://tempuri.org">  
   <q:bodyX xmlns:q="http://tempuri.org">test</q:bodyX>  
</replyDefault>  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les échantillons de la Fondation De communication Windows.](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)  
  
2. Pour construire la solution, suivez les instructions dans [la construction des échantillons de la Fondation De communication Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Pour exécuter l’échantillon dans une configuration mono-ou cross-machine, suivez les instructions dans [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons. Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\AdvancedDispatchByBody`  
