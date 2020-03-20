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
# <a name="dispatch-by-body-element"></a><span data-ttu-id="d33f8-102">Dispatch by Body Element</span><span class="sxs-lookup"><span data-stu-id="d33f8-102">Dispatch by Body Element</span></span>
<span data-ttu-id="d33f8-103">Cet exemple montre comment implémenter un autre algorithme pour l'assignation des messages entrants aux opérations.</span><span class="sxs-lookup"><span data-stu-id="d33f8-103">This sample demonstrates how to implement an alternate algorithm for assigning incoming messages to operations.</span></span>  
  
 <span data-ttu-id="d33f8-104">Par défaut, le répartiteur modèle de service sélectionne la méthode de gestion appropriée pour un message entrant en fonction de l'en-tête d'action WS-Addressing du message ou de l'information équivalente dans la requête HTTP SOAP.</span><span class="sxs-lookup"><span data-stu-id="d33f8-104">By default, the service model dispatcher selects the appropriate handling method for an incoming message based on the message's WS-Addressing "Action" header or the equivalent information in the HTTP SOAP request.</span></span>  
  
 <span data-ttu-id="d33f8-105">Quelques piles de services Web SOAP 1.1 qui ne suivent pas les indications du profil WS-I Basic Profile 1.1 ne distribuent pas les messages en fonction de l'URI d'action, mais plutôt selon le nom qualifié XML du premier élément contenu dans le corps SOAP.</span><span class="sxs-lookup"><span data-stu-id="d33f8-105">Some SOAP 1.1 Web services stacks that do not follow the WS-I Basic Profile 1.1 guidelines do not dispatch messages based on the Action URI, but rather based on the XML qualified name of the first element inside the SOAP body.</span></span> <span data-ttu-id="d33f8-106">De même, le côté client de ces piles peut envoyer des messages avec un en-tête HTTP SoapAction vide ou arbitraire ayant été autorisé par la spécification SOAP 1.1.</span><span class="sxs-lookup"><span data-stu-id="d33f8-106">Likewise, the client side of these stacks might send messages with an empty or arbitrary HTTP SoapAction header, which was permitted by the SOAP 1.1 specification.</span></span>  
  
 <span data-ttu-id="d33f8-107">Pour modifier le mode de distribution des messages aux méthodes, l'exemple implémente l'interface d'extensibilité <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> sur le `DispatchByBodyElementOperationSelector`.</span><span class="sxs-lookup"><span data-stu-id="d33f8-107">To change the way messages are dispatched to methods, the sample implements the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> extensibility interface on the `DispatchByBodyElementOperationSelector`.</span></span> <span data-ttu-id="d33f8-108">Cette classe sélectionne des opérations en fonction du premier élément du corps du message.</span><span class="sxs-lookup"><span data-stu-id="d33f8-108">This class selects operations based on the first element of the message body.</span></span>  
  
 <span data-ttu-id="d33f8-109">Le constructeur de classe attend un dictionnaire rempli avec les paires de `XmlQualifiedName` et les chaînes, dans lequel les noms qualifiés indiquent le nom du premier enfant du corps SOAP et les chaînes indiquent le nom d'opération correspondant.</span><span class="sxs-lookup"><span data-stu-id="d33f8-109">The class constructor expects a dictionary populated with pairs of `XmlQualifiedName` and strings, whereby the qualified names indicate the name of the first child of the SOAP body and the strings indicate the matching operation name.</span></span> <span data-ttu-id="d33f8-110">`defaultOperationName` est le nom de l'opération qui reçoit tous les messages qui ne peuvent pas être comparés à ce dictionnaire:</span><span class="sxs-lookup"><span data-stu-id="d33f8-110">The `defaultOperationName` is the name of the operation that receives all messages that cannot be matched against this dictionary:</span></span>  
  
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
  
 <span data-ttu-id="d33f8-111">Les implémentations d'<xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> sont très simples à générer puisqu'une seule méthode est présente sur l'interface : <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A>.</span><span class="sxs-lookup"><span data-stu-id="d33f8-111"><xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementations are very straightforward to build as there is only one method on the interface: <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A>.</span></span> <span data-ttu-id="d33f8-112">Le rôle de cette méthode consiste à inspecter un message entrant et à retourner une chaîne égale au nom d'une méthode sur le contrat de service pour le point de terminaison actuel.</span><span class="sxs-lookup"><span data-stu-id="d33f8-112">The job of this method is to inspect an incoming message and to return a string that equals the name of a method on the service contract for the current endpoint.</span></span>  
  
 <span data-ttu-id="d33f8-113">Dans cet exemple, le sélecteur d'opération acquiert une classe <xref:System.Xml.XmlDictionaryReader> pour le corps du message entrant à l'aide de <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>.</span><span class="sxs-lookup"><span data-stu-id="d33f8-113">In this sample, the operation selector acquires an <xref:System.Xml.XmlDictionaryReader> for the incoming message's body using <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>.</span></span> <span data-ttu-id="d33f8-114">Cette méthode positionne déjà le lecteur sur le premier enfant du corps du message afin que ce soit suffisant pour obtenir le nom de l'élément actuel et l'URI d'espace de noms, et les mixer dans un `XmlQualifiedName` utilisé ensuite pour voir l'opération correspondante du dictionnaire tenu par le sélecteur d'opération.</span><span class="sxs-lookup"><span data-stu-id="d33f8-114">This method already positions the reader on the first child of the message's body so that it is sufficient to get the current element's name and namespace URI and combine them into an `XmlQualifiedName` that is then used for looking up the corresponding operation from the dictionary held by the operation selector.</span></span>  
  
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
  
 <span data-ttu-id="d33f8-115">L'accès au corps du message avec <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> ou l'une des autres méthodes qui fournissent l'accès au contenu de corps du message entraîne le marquage du message comme lu, ce qui signifie que ce dernier n'est pas valide pour tout traitement ultérieur.</span><span class="sxs-lookup"><span data-stu-id="d33f8-115">Accessing the message body with <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> or any of the other methods that provide access to the message's body content causes the message to be marked as "read", which means that the message is invalid for any further processing.</span></span> <span data-ttu-id="d33f8-116">Par conséquent, le sélecteur d'opération crée une copie du message entrant avec la méthode affichée dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="d33f8-116">Therefore, the operation selector creates a copy of the incoming message with the method shown in the following code.</span></span> <span data-ttu-id="d33f8-117">Parce que la position du lecteur n'a pas été modifiée au cours de l'inspection, elle peut être référencée par le message nouvellement créé et dans lequel les propriétés et en-têtes de message sont également copiés, ce qui génère un clone exact du message d'origine :</span><span class="sxs-lookup"><span data-stu-id="d33f8-117">Because the reader's position has not been changed during the inspection, it can be referenced by the newly created message to which the message properties and the message headers are also copied, which results in an exact clone of the original message:</span></span>  
  
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
  
## <a name="adding-an-operation-selector-to-a-service"></a><span data-ttu-id="d33f8-118">Ajout d'un sélecteur d'opération à un service</span><span class="sxs-lookup"><span data-stu-id="d33f8-118">Adding an Operation Selector to a Service</span></span>  
 <span data-ttu-id="d33f8-119">Les sélecteurs d’opérations de répartition des services sont des extensions au répartiteur de la Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="d33f8-119">Service dispatch operation selectors are extensions to the Windows Communication Foundation (WCF) dispatcher.</span></span> <span data-ttu-id="d33f8-120">Pour la sélection des méthodes sur le canal de rappel de contrats duplex, il existe également des sélecteurs d'opération clients qui fonctionnent de manière semblable aux sélecteurs d'opération de distribution décrits ici, mais ne sont pas traités de manière explicite dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="d33f8-120">For selecting methods on the callback channel of duplex contracts, there are also client operation selectors, which work very much like the dispatch operation selectors described here, but which are not explicitly covered in this sample.</span></span>  
  
 <span data-ttu-id="d33f8-121">Comme la plupart des extensions de modèle de service, les sélecteurs d’opération de distribution sont ajoutés au répartiteur à l’aide de comportements.</span><span class="sxs-lookup"><span data-stu-id="d33f8-121">Like most service model extensions, dispatch operation selectors are added to the dispatcher using behaviors.</span></span> <span data-ttu-id="d33f8-122">Un *comportement* est un objet de configuration, qui ajoute une ou plusieurs extensions au temps d’exécution de l’expédition (ou au temps d’exécution du client) ou modifie autrement ses paramètres.</span><span class="sxs-lookup"><span data-stu-id="d33f8-122">A *behavior* is a configuration object, which either adds one or more extensions to the dispatch runtime (or to the client runtime) or otherwise changes its settings.</span></span>  
  
 <span data-ttu-id="d33f8-123">Parce que les sélecteurs d'opération disposent d'une étendue de contrat, <xref:System.ServiceModel.Description.IContractBehavior> est le comportement approprié à implémenter ici.</span><span class="sxs-lookup"><span data-stu-id="d33f8-123">Because operation selectors have contract scope, the appropriate behavior to implement here is the <xref:System.ServiceModel.Description.IContractBehavior>.</span></span> <span data-ttu-id="d33f8-124">Étant donné que l'interface est implémentée sur une classe dérivée <xref:System.Attribute> comme indiqué dans le code suivant, le comportement peut être ajouté de façon déclarative à tout contrat de service.</span><span class="sxs-lookup"><span data-stu-id="d33f8-124">Because the interface is implemented on a <xref:System.Attribute> derived class as shown in the following code, the behavior can be declaratively added to any service contract.</span></span> <span data-ttu-id="d33f8-125">Chaque fois qu’une classe <xref:System.ServiceModel.ServiceHost> est ouverte et que l’exécution du répartiteur est générée, tous les comportements recherchés, soit en tant qu’attributs sur les contrats, opérations et implémentations de service, soit en tant qu’élément dans la configuration du service, sont automatiquement ajoutés et doivent ensuite fournir des extensions ou modifier la configuration par défaut.</span><span class="sxs-lookup"><span data-stu-id="d33f8-125">Whenever a <xref:System.ServiceModel.ServiceHost> is opened and the dispatch runtime is built, all behaviors found either as attributes on contracts, operations, and service implementations or as element in the service configuration are automatically added and subsequently asked to contribute extensions or modify the default configuration.</span></span>  
  
 <span data-ttu-id="d33f8-126">Pour des raisons de concision, l'extrait de code suivant affiche seulement l'implémentation de la méthode <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> qui effectue les modifications de configuration du répartiteur dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="d33f8-126">For brevity, the following code excerpt only shows the implementation of the method <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A>, which effects the configuration changes for the dispatcher in this sample.</span></span> <span data-ttu-id="d33f8-127">Les autres méthodes ne sont pas indiquées car elles sont retournées à l'appelant sans effectuer aucun travail.</span><span class="sxs-lookup"><span data-stu-id="d33f8-127">The other methods are not shown because they return to the caller without doing any work.</span></span>  
  
```csharp
[AttributeUsage(AttributeTargets.Class|AttributeTargets.Interface)]  
class DispatchByBodyElementBehaviorAttribute : Attribute, IContractBehavior  
{  
    // public void AddBindingParameters(...)
    // public void ApplyClientBehavior(...)  
    // public void Validate(...)  
```  
  
 <span data-ttu-id="d33f8-128">En premier lieu, l'implémentation <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> installe le dictionnaire de recherche pour le sélecteur d'opération en itérant sur les éléments <xref:System.ServiceModel.Description.OperationDescription> dans la classe <xref:System.ServiceModel.Description.ContractDescription> du point de terminaison de service.</span><span class="sxs-lookup"><span data-stu-id="d33f8-128">First, the <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> implementation sets up the lookup dictionary for the operation selector by iterating over the <xref:System.ServiceModel.Description.OperationDescription> elements in the service endpoint's <xref:System.ServiceModel.Description.ContractDescription>.</span></span> <span data-ttu-id="d33f8-129">Ensuite, la présence du comportement `DispatchBodyElementAttribute` (une implémentation de <xref:System.ServiceModel.Description.IOperationBehavior> qui est également défini dans cet exemple) est vérifiée dans chaque description d'opération.</span><span class="sxs-lookup"><span data-stu-id="d33f8-129">Then, each operation description is inspected for the presence of the `DispatchBodyElementAttribute` behavior, an implementation of <xref:System.ServiceModel.Description.IOperationBehavior> that is also defined in this sample.</span></span> <span data-ttu-id="d33f8-130">Bien que cette classe constitue également un comportement, elle est passive et ne fournit pas de manière active de modifications de configuration apportées à l'exécution du répartiteur.</span><span class="sxs-lookup"><span data-stu-id="d33f8-130">While this class is also a behavior, it is passive and does not actively contribute any configuration changes to the dispatch runtime.</span></span> <span data-ttu-id="d33f8-131">Toutes ses méthodes sont retournées à l'appelant sans aucune action.</span><span class="sxs-lookup"><span data-stu-id="d33f8-131">All of its methods return to the caller without taking any actions.</span></span> <span data-ttu-id="d33f8-132">Le comportement d'opération existe seulement afin que les métadonnées requises pour le nouveau mécanisme de distribution, à savoir le nom qualifié de l'élément de corps sur lequel une opération est sélectionnée, puissent être associées aux opérations respectives.</span><span class="sxs-lookup"><span data-stu-id="d33f8-132">The operation behavior only exists so that the metadata required for the new dispatch mechanism, namely the qualified name of the body element on whose occurrence an operation is selected, can be associated with the respective operations.</span></span>  
  
 <span data-ttu-id="d33f8-133">Si ce comportement est trouvé, une paire valeur créée à partir du nom qualifié XML (propriété `QName`) et le nom d'opération (propriété `Name`) sont ajoutés au dictionnaire.</span><span class="sxs-lookup"><span data-stu-id="d33f8-133">If such a behavior is found, a value pair created from the XML qualified name (`QName` property) and the operation name (`Name` property) is added to the dictionary.</span></span>  
  
 <span data-ttu-id="d33f8-134">Une fois le dictionnaire rempli, un nouveau `DispatchByBodyElementOperationSelector` est généré avec ces informations et défini comme le sélecteur d'opération de l'exécution du répartiteur :</span><span class="sxs-lookup"><span data-stu-id="d33f8-134">Once the dictionary is populated, a new `DispatchByBodyElementOperationSelector` is constructed with this information and set as the operation selector of the dispatch runtime:</span></span>  
  
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
  
## <a name="implementing-the-service"></a><span data-ttu-id="d33f8-135">Implémentation du service</span><span class="sxs-lookup"><span data-stu-id="d33f8-135">Implementing the Service</span></span>  
 <span data-ttu-id="d33f8-136">Le comportement implémenté dans cet exemple affecte directement la façon dont les messages provenant du câble sont interprétés et distribués, ce qui constitue une fonction du contrat de service.</span><span class="sxs-lookup"><span data-stu-id="d33f8-136">The behavior implemented in this sample directly affects how messages from the wire are interpreted and dispatched, which is a function of the service contract.</span></span> <span data-ttu-id="d33f8-137">Par conséquent, le comportement doit être déclaré sur le niveau de contrat de service dans toute implémentation de service qui choisit de l'utiliser.</span><span class="sxs-lookup"><span data-stu-id="d33f8-137">Consequently, the behavior should be declared on the service contract level in any service implementation that chooses to use it.</span></span>  
  
 <span data-ttu-id="d33f8-138">Le service de `DispatchByBodyElementBehaviorAttribute` projet d’échantillon applique le comportement du `OperationForBodyA()` `OperationForBodyB()` contrat `DispatchBodyElementAttribute` au `IDispatchedByBody` contrat de service et étiquette chacune des deux opérations et avec un comportement d’opération.</span><span class="sxs-lookup"><span data-stu-id="d33f8-138">The sample project service applies the `DispatchByBodyElementBehaviorAttribute` contract behavior to the `IDispatchedByBody` service contract and labels each of the two operations `OperationForBodyA()` and `OperationForBodyB()` with a `DispatchBodyElementAttribute` operation behavior.</span></span> <span data-ttu-id="d33f8-139">Lorsqu'un hôte est ouvert pour un service qui implémente ce contrat, ces métadonnées sont choisies par le générateur de répartiteurs comme décrit précédemment.</span><span class="sxs-lookup"><span data-stu-id="d33f8-139">When a service host for a service that implements this contract is opened, this metadata is picked up by the dispatcher builder as previously described.</span></span>  
  
 <span data-ttu-id="d33f8-140">Étant donné que le sélecteur d'opération effectue la distribution uniquement en fonction l'élément de corps du message et ignore l'en-tête Action, il doit indiquer au runtime de ne pas vérifier cet en-tête sur les réponses retournées en assignant le caractère générique « \* » à la propriété `ReplyAction` de la classe <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="d33f8-140">Because the operation selector dispatches solely based on the message body element and ignores the "Action", it is required to tell the runtime not to check the "Action" header on the returned replies by assigning the wildcard "\*" to the `ReplyAction` property of <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="d33f8-141">En outre, il est nécessaire d’avoir une opération par défaut\*qui a la propriété "Action" réglé à la wildcard ".</span><span class="sxs-lookup"><span data-stu-id="d33f8-141">Furthermore, it is required to have a default operation that has the "Action" property set to the wildcard "\*".</span></span> <span data-ttu-id="d33f8-142">L'opération par défaut reçoit tous les messages qui ne peuvent pas être distribués et n'ont pas de `DispatchBodyElementAttribute` :</span><span class="sxs-lookup"><span data-stu-id="d33f8-142">The default operation receives all messages which cannot be dispatched and does not have a `DispatchBodyElementAttribute`:</span></span>  
  
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
  
 <span data-ttu-id="d33f8-143">L'implémentation du service exemple est simple.</span><span class="sxs-lookup"><span data-stu-id="d33f8-143">The sample service implementation is straightforward.</span></span> <span data-ttu-id="d33f8-144">Chaque méthode insère le message reçu dans un message de réponse et le retourne au client.</span><span class="sxs-lookup"><span data-stu-id="d33f8-144">Every method wraps the received message into a reply message and echoes it back to the client.</span></span>  
  
## <a name="running-and-building-the-sample"></a><span data-ttu-id="d33f8-145">Génération et exécution de l'exemple</span><span class="sxs-lookup"><span data-stu-id="d33f8-145">Running and Building the Sample</span></span>  
 <span data-ttu-id="d33f8-146">Lorsque vous exécutez l'exemple, le contenu du corps des réponses d'opération est affiché dans la fenêtre de la console cliente semblable à la sortie suivante (mis en forme).</span><span class="sxs-lookup"><span data-stu-id="d33f8-146">When you run the sample, the body content of the operation responses are displayed in the client console window similar to the following (formatted) output.</span></span>  
  
 <span data-ttu-id="d33f8-147">Le client envoie trois messages au service dont l'élément du contenu du corps est nommé `bodyA`, `bodyB` et `bodyX`, respectivement.</span><span class="sxs-lookup"><span data-stu-id="d33f8-147">The client sends three messages to the service whose body content element is named `bodyA`, `bodyB`, and `bodyX`, respectively.</span></span> <span data-ttu-id="d33f8-148">Comme il peut être différé de la description précédente et du contrat de service indiqué, le message entrant avec l'élément `bodyA` est distribué à la méthode `OperationForBodyA()`.</span><span class="sxs-lookup"><span data-stu-id="d33f8-148">As can be deferred from the previous description and the service contract shown, the incoming message with the `bodyA` element is dispatched to the `OperationForBodyA()` method.</span></span> <span data-ttu-id="d33f8-149">Étant donné qu'il n'y a aucune cible de distribution explicite pour le message avec l'élément de corps `bodyX`, le message est distribué à `DefaultOperation()`.</span><span class="sxs-lookup"><span data-stu-id="d33f8-149">Because there is no explicit dispatch target for the message with the `bodyX` body element, the message is dispatched to the `DefaultOperation()`.</span></span> <span data-ttu-id="d33f8-150">Chacune des opérations de service englobe le corps du message reçu dans un élément spécifique à la méthode et le renvoie, ce qui permet de faire correspondre clairement les messages d'entrée et de sortie pour cet exemple :</span><span class="sxs-lookup"><span data-stu-id="d33f8-150">Each of the service operations wraps the received message body into an element specific to the method and returns it, which is done to correlate input and output messages clearly for this sample:</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d33f8-151">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="d33f8-151">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="d33f8-152">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les échantillons de la Fondation De communication Windows.](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)</span><span class="sxs-lookup"><span data-stu-id="d33f8-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="d33f8-153">Pour construire la solution, suivez les instructions dans [la construction des échantillons de la Fondation De communication Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d33f8-153">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="d33f8-154">Pour exécuter l’échantillon dans une configuration mono-ou cross-machine, suivez les instructions dans [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d33f8-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d33f8-155">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d33f8-155">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d33f8-156">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="d33f8-156">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="d33f8-157">Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons.</span><span class="sxs-lookup"><span data-stu-id="d33f8-157">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d33f8-158">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="d33f8-158">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\AdvancedDispatchByBody`  
