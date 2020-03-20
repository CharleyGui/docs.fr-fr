---
title: Operation Formatter and Operation Selector
ms.date: 03/30/2017
ms.assetid: 1c27e9fe-11f8-4377-8140-828207b98a0e
ms.openlocfilehash: 9d1bc0afa54f89e064eab3f3e45da60c8d10de38
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144277"
---
# <a name="operation-formatter-and-operation-selector"></a><span data-ttu-id="b3e67-102">Operation Formatter and Operation Selector</span><span class="sxs-lookup"><span data-stu-id="b3e67-102">Operation Formatter and Operation Selector</span></span>
<span data-ttu-id="b3e67-103">Cet exemple montre comment les points d’extabilité de la Windows Communication Foundation (WCF) peuvent être utilisés pour permettre des données de message dans un format différent de ce que WCF attend.</span><span class="sxs-lookup"><span data-stu-id="b3e67-103">This sample demonstrates how Windows Communication Foundation (WCF) extensibility points can be used to allow message data in a different format from what WCF expects.</span></span> <span data-ttu-id="b3e67-104">Par défaut, les formateurs WCF s’attendent `soap:body` à ce que les paramètres de méthode soient inclus dans l’élément.</span><span class="sxs-lookup"><span data-stu-id="b3e67-104">By default, WCF formatters expect method parameters to be included under the `soap:body` element.</span></span> <span data-ttu-id="b3e67-105">L'exemple montre comment implémenter à la place un formateur d'opération personnalisé qui analyse les données de paramètre d'une chaîne de requête HTTP GET chaîne et appelle des méthodes à l'aide de ces données.</span><span class="sxs-lookup"><span data-stu-id="b3e67-105">The sample shows how to implement a custom operation formatter that parses parameter data from an HTTP GET query string instead and invokes methods using that data.</span></span>  
  
 <span data-ttu-id="b3e67-106">L’échantillon est basé sur le Getting `ICalculator` [Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), qui met en œuvre le contrat de service.</span><span class="sxs-lookup"><span data-stu-id="b3e67-106">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="b3e67-107">Il montre comment les messages d'ajout, de soustraction, de multiplication et de division peuvent être modifiés pour utiliser HTTP GET pour les demandes de client à serveur et HTTP POST avec messages POX pour les réponses de serveur à client.</span><span class="sxs-lookup"><span data-stu-id="b3e67-107">It shows how Add, Subtract, Multiply, and Divide messages can be changed to use HTTP GET for client-to-server requests and HTTP POST with POX messages for server-to-client responses.</span></span>  
  
 <span data-ttu-id="b3e67-108">Pour cela, l'exemple fournit les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="b3e67-108">To do so, the sample provides the following:</span></span>  
  
- <span data-ttu-id="b3e67-109">`QueryStringFormatter`, qui implémente <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> et <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> pour le client et le serveur respectivement, et traite les données dans la chaîne de requête.</span><span class="sxs-lookup"><span data-stu-id="b3e67-109">`QueryStringFormatter`, which implements <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> and <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> for the client and server, respectively, and processes the data in the query string.</span></span>  
  
- <span data-ttu-id="b3e67-110">`UriOperationSelector`, qui implémente <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> sur le serveur pour effectuer la distribution des opérations en fonction du nom de l'opération dans la demande GET.</span><span class="sxs-lookup"><span data-stu-id="b3e67-110">`UriOperationSelector`, which implements <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> on the server to perform operation dispatch based on the operation name in the GET request.</span></span>  
  
- <span data-ttu-id="b3e67-111">Comportement de point de terminaison `EnableHttpGetRequestsBehavior` (et configuration correspondante), qui ajoute le sélecteur d'opération nécessaire à l'exécution.</span><span class="sxs-lookup"><span data-stu-id="b3e67-111">`EnableHttpGetRequestsBehavior` endpoint behavior (and corresponding configuration), which adds the necessary operation selector to the runtime.</span></span>  
  
- <span data-ttu-id="b3e67-112">Indique comment insérer un nouveau formateur d'opération dans l'exécution.</span><span class="sxs-lookup"><span data-stu-id="b3e67-112">Shows how to insert a new operation formatter into the runtime.</span></span>  
  
- <span data-ttu-id="b3e67-113">Dans cet exemple, le client et le service sont tous deux des applications consoles (.exe).</span><span class="sxs-lookup"><span data-stu-id="b3e67-113">In this sample, both the client and the service are console applications (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b3e67-114">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="b3e67-114">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="key-concepts"></a><span data-ttu-id="b3e67-115">Concepts clés</span><span class="sxs-lookup"><span data-stu-id="b3e67-115">Key Concepts</span></span>  
 <span data-ttu-id="b3e67-116">`QueryStringFormatter`- Le formateur d’opération est le composant de WCF qui est responsable de la conversion d’un message en un tableau d’objets paramètres et une gamme d’objets paramètres en un message.</span><span class="sxs-lookup"><span data-stu-id="b3e67-116">`QueryStringFormatter` - The operation formatter is the component in WCF that is responsible for converting a message into an array of parameter objects and an array of parameter objects into a message.</span></span> <span data-ttu-id="b3e67-117">Cela est effectué sur le client à l'aide de l'interface <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> et sur le serveur avec l'interface <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>.</span><span class="sxs-lookup"><span data-stu-id="b3e67-117">This is done on the client using the <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> interface and on the server with the <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interface.</span></span> <span data-ttu-id="b3e67-118">Ces interfaces permettent aux utilisateurs d'obtenir les messages de demande et de réponse des méthodes `Serialize` et `Deserialize`.</span><span class="sxs-lookup"><span data-stu-id="b3e67-118">These interfaces enable users to get the request and response messages from the `Serialize` and `Deserialize` methods.</span></span>  
  
 <span data-ttu-id="b3e67-119">Dans cet exemple, `QueryStringFormatter` implémente ces deux interfaces et est implémenté sur le client et le serveur.</span><span class="sxs-lookup"><span data-stu-id="b3e67-119">In this sample, `QueryStringFormatter` implements both of these interfaces and is implemented on the client and server.</span></span>  
  
 <span data-ttu-id="b3e67-120">Demande :</span><span class="sxs-lookup"><span data-stu-id="b3e67-120">Request:</span></span>  
  
- <span data-ttu-id="b3e67-121">L'exemple utilise la classe <xref:System.ComponentModel.TypeConverter> pour convertir les données de paramètre du message de demande en chaînes et vice versa.</span><span class="sxs-lookup"><span data-stu-id="b3e67-121">The sample uses the <xref:System.ComponentModel.TypeConverter> class to convert parameter data in the request message to and from strings.</span></span> <span data-ttu-id="b3e67-122">Si un <xref:System.ComponentModel.TypeConverter> n'est pas disponible pour un type spécifique, l'exemple de formateur lève une exception.</span><span class="sxs-lookup"><span data-stu-id="b3e67-122">If a <xref:System.ComponentModel.TypeConverter> is not available for a specific type, the sample formatter throws an exception.</span></span>  
  
- <span data-ttu-id="b3e67-123">Dans la méthode `IClientMessageFormatter.SerializeRequest` sur le client, le formateur crée un URI avec l''adresse To appropriée et ajoute le nom d'opération en tant que suffixe.</span><span class="sxs-lookup"><span data-stu-id="b3e67-123">In the `IClientMessageFormatter.SerializeRequest` method on the client, the formatter creates a URI with the appropriate To address and appends the operation name as a suffix.</span></span> <span data-ttu-id="b3e67-124">Ce nom est utilisé pour la distribution à l'opération appropriée sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="b3e67-124">This name is used to dispatch to the appropriate operation on the server.</span></span> <span data-ttu-id="b3e67-125">Il prend ensuite le tableau d'objets de paramètre et sérialise les données de paramètre dans la chaîne de requête URI à l'aide des noms de paramètre et des valeurs converties par la classe <xref:System.ComponentModel.TypeConverter>.</span><span class="sxs-lookup"><span data-stu-id="b3e67-125">It then takes the array of parameter objects and serializes the parameter data to the URI query string using parameter names and the values converted by the <xref:System.ComponentModel.TypeConverter> class.</span></span> <span data-ttu-id="b3e67-126">Cette valeur est affectée aux propriétés <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> et <xref:System.ServiceModel.Channels.MessageProperties.Via%2A>, puis à cet URI.</span><span class="sxs-lookup"><span data-stu-id="b3e67-126">The <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> and <xref:System.ServiceModel.Channels.MessageProperties.Via%2A> properties are then set to this URI.</span></span> <span data-ttu-id="b3e67-127"><xref:System.ServiceModel.Channels.MessageProperties> est accessible à l'aide de la propriété <xref:System.ServiceModel.Channels.Message.Properties%2A>.</span><span class="sxs-lookup"><span data-stu-id="b3e67-127"><xref:System.ServiceModel.Channels.MessageProperties> is accessed through the <xref:System.ServiceModel.Channels.Message.Properties%2A> property.</span></span>  
  
- <span data-ttu-id="b3e67-128">Dans la méthode `IDispatchMessageFormatter.DeserializeRequest` sur le serveur, le formateur récupère l'URI `Via` dans les propriétés de message de la demande entrante.</span><span class="sxs-lookup"><span data-stu-id="b3e67-128">In the `IDispatchMessageFormatter.DeserializeRequest` method on the server, the formatter retrieves the `Via` URI in the incoming request message properties.</span></span> <span data-ttu-id="b3e67-129">Il analyse les paires nom-valeur dans la chaîne de requête URI en fonction des noms de paramètre et des valeurs et utilise les noms de paramètre et les valeurs pour compléter le tableau de paramètres passé dans la méthode.</span><span class="sxs-lookup"><span data-stu-id="b3e67-129">It parses the name-value pairs in the URI query string into parameter names and values and uses the parameter names and values to populate the array of parameters passed into the method.</span></span> <span data-ttu-id="b3e67-130">Notez que la distribution des opérations s'est déjà produite, donc le suffixe du nom de l'opération est ignoré dans cette méthode.</span><span class="sxs-lookup"><span data-stu-id="b3e67-130">Note that operation dispatch has already occurred, so the operation name suffix is ignored in this method.</span></span>  
  
 <span data-ttu-id="b3e67-131">Réponse :</span><span class="sxs-lookup"><span data-stu-id="b3e67-131">Response:</span></span>  
  
- <span data-ttu-id="b3e67-132">Dans cet exemple, HTTP GET est utilisé uniquement pour la demande.</span><span class="sxs-lookup"><span data-stu-id="b3e67-132">In this sample, HTTP GET is used only for the request.</span></span> <span data-ttu-id="b3e67-133">Le formateur délègue l'envoi de la réponse au formateur d'origine qui aurait été utilisé pour générer un message XML.</span><span class="sxs-lookup"><span data-stu-id="b3e67-133">The formatter delegates the sending of the response to the original formatter that would have been used to generate an XML message.</span></span> <span data-ttu-id="b3e67-134">L'un des objectifs de cet exemple est de montrer comment un tel formateur déléguant peut être implémenté.</span><span class="sxs-lookup"><span data-stu-id="b3e67-134">One of the goals of this sample is to show how such a delegating formatter can be implemented.</span></span>  
  
### <a name="uripathsuffixoperationselector-class"></a><span data-ttu-id="b3e67-135">Classe UriPathSuffixOperationSelector</span><span class="sxs-lookup"><span data-stu-id="b3e67-135">UriPathSuffixOperationSelector Class</span></span>  
 <span data-ttu-id="b3e67-136">L'interface <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> permet aux utilisateurs d'implémenter leur propre logique pour indiquer pour quelle opération un message particulier doit être distribué.</span><span class="sxs-lookup"><span data-stu-id="b3e67-136">The <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> interface enables users to implement their own logic for which operation a particular message should be dispatched.</span></span>  
  
 <span data-ttu-id="b3e67-137">Dans cet exemple, `UriPathSuffixOperationSelector` doit être implémenté sur le serveur pour sélectionner l'opération appropriée parce que le nom de l'opération est inclus dans l'URI HTTP GET plutôt que dans un en-tête d'action dans le message.</span><span class="sxs-lookup"><span data-stu-id="b3e67-137">In this sample, `UriPathSuffixOperationSelector` must be implemented on the server to select the appropriate operation because the operation name is included in the HTTP GET URI rather than an action header in the message.</span></span> <span data-ttu-id="b3e67-138">L'exemple est configuré pour des noms d'opération non sensibles à la casse uniquement.</span><span class="sxs-lookup"><span data-stu-id="b3e67-138">The sample is set up to allow only case-insensitive operation names.</span></span>  
  
 <span data-ttu-id="b3e67-139">La méthode `SelectOperation` prend le message entrant et recherche l'URI `Via` dans ses propriétés de message.</span><span class="sxs-lookup"><span data-stu-id="b3e67-139">The `SelectOperation` method takes the incoming message and looks up the `Via` URI in its message properties.</span></span> <span data-ttu-id="b3e67-140">Elle extrait le suffixe du nom de l'opération de l'URI, recherche une table interne pour obtenir le nom de l'opération à laquelle le message doit être distribué, et retourne ce nom d'opération.</span><span class="sxs-lookup"><span data-stu-id="b3e67-140">It extracts the operation name suffix from the URI, looks up an internal table to get the operation name that the message should be dispatched to, and returns that operation name.</span></span>  
  
### <a name="enablehttpgetrequestsbehavior-class"></a><span data-ttu-id="b3e67-141">Classe EnableHttpGetRequestsBehavior</span><span class="sxs-lookup"><span data-stu-id="b3e67-141">EnableHttpGetRequestsBehavior Class</span></span>  
 <span data-ttu-id="b3e67-142">Le composant `UriPathSuffixOperationSelector` peut être installé par programme ou par l'intermédiaire d'un comportement de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="b3e67-142">The `UriPathSuffixOperationSelector` component can be set up programmatically or through an endpoint behavior.</span></span> <span data-ttu-id="b3e67-143">L'exemple implémente le comportement `EnableHttpGetRequestsBehavior`, spécifié dans le fichier de configuration de l'application du service.</span><span class="sxs-lookup"><span data-stu-id="b3e67-143">The sample implements the `EnableHttpGetRequestsBehavior` behavior, which is specified in service’s application configuration file.</span></span>  
  
 <span data-ttu-id="b3e67-144">Sur le serveur :</span><span class="sxs-lookup"><span data-stu-id="b3e67-144">On the server:</span></span>  
  
 <span data-ttu-id="b3e67-145">Le <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> a pour valeur l'implémentation <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector>.</span><span class="sxs-lookup"><span data-stu-id="b3e67-145">The <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> is set to the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementation.</span></span>  
  
 <span data-ttu-id="b3e67-146">Par défaut, WCF utilise un filtre d’adresse exact-match.</span><span class="sxs-lookup"><span data-stu-id="b3e67-146">By default, WCF uses an exact-match address filter.</span></span> <span data-ttu-id="b3e67-147">L'URI sur le message entrant contient un suffixe de nom d'opération suivi par une chaîne de requête qui contient des données de paramètre, donc le comportement de point de terminaison modifie également le filtre d'adresse en filtre de correspondance du préfixe.</span><span class="sxs-lookup"><span data-stu-id="b3e67-147">The URI on the incoming message contains an operation name suffix followed by a query string that contains parameter data, so the endpoint behavior also changes the address filter to be a prefix match filter.</span></span> <span data-ttu-id="b3e67-148">Il utilise le<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> WCF à cette fin.</span><span class="sxs-lookup"><span data-stu-id="b3e67-148">It uses the WCF<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> for this purpose.</span></span>  
  
### <a name="installing-operation-formatters"></a><span data-ttu-id="b3e67-149">Installation des formateurs d'opération</span><span class="sxs-lookup"><span data-stu-id="b3e67-149">Installing operation formatters</span></span>  
 <span data-ttu-id="b3e67-150">Les comportements d'opération qui spécifient des formateurs sont uniques.</span><span class="sxs-lookup"><span data-stu-id="b3e67-150">Operation behaviors that specify formatters are unique.</span></span> <span data-ttu-id="b3e67-151">Un tel comportement est toujours implémenté par défaut pour chaque opération pour créer le formateur d'opération nécessaire.</span><span class="sxs-lookup"><span data-stu-id="b3e67-151">One such behavior is always implemented by default for every operation to create the necessary operation formatter.</span></span> <span data-ttu-id="b3e67-152">Toutefois, ces comportements ressemblent à tous les autres comportements d'opération ; ils ne sont pas identifiables par tout autre attribut.</span><span class="sxs-lookup"><span data-stu-id="b3e67-152">However, these behaviors look like just another operation behavior; they are not identifiable by any other attribute.</span></span> <span data-ttu-id="b3e67-153">Pour installer un comportement de remplacement, l’implémentation doit rechercher des comportements de formateur spécifiques qui sont installés par le chargeur de type WCF par défaut et soit le remplacer ou ajouter un comportement compatible pour fonctionner après le comportement par défaut.</span><span class="sxs-lookup"><span data-stu-id="b3e67-153">To install a replacement behavior, the implementation must look for specific formatter behaviors that are installed by the WCF type loader by default and either replace it or add a compatible behavior to run after the default behavior.</span></span>  
  
 <span data-ttu-id="b3e67-154">Ces comportements de formateur d'opération peuvent être installés par programme avant d'appeler <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> ou en spécifiant un comportement d'opération exécuté après le comportement par défaut.</span><span class="sxs-lookup"><span data-stu-id="b3e67-154">These operation formatters behaviors can be set up programmatically prior to calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> or by specifying an operation behavior that is executed after the default one.</span></span> <span data-ttu-id="b3e67-155">Cependant, ils ne peuvent pas être installés facilement par un comportement de point de terminaison (et par conséquent par la configuration) parce que le modèle de comportement ne permet pas à un comportement de remplacer d’autres comportements ou modifier de toute autre manière l’arborescence de description.</span><span class="sxs-lookup"><span data-stu-id="b3e67-155">However, it cannot easily be set up by an endpoint behavior (and therefore by configuration) because the behavior model does not allow a behavior to replace other behaviors or otherwise modify the description tree.</span></span>  
  
 <span data-ttu-id="b3e67-156">Sur le client :</span><span class="sxs-lookup"><span data-stu-id="b3e67-156">On the client:</span></span>  
  
 <span data-ttu-id="b3e67-157">L'implémentation <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> doit être implémentée afin qu'elle puisse convertir les demandes en demandes HTTP GET et déléguer les réponses au formateur d'origine.</span><span class="sxs-lookup"><span data-stu-id="b3e67-157">The <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> implementation must be implemented so that it can convert the requests into HTTP GET requests and delegate to the original formatter for responses.</span></span> <span data-ttu-id="b3e67-158">Cela est effectué en appelant la méthode d'assistance `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior`.</span><span class="sxs-lookup"><span data-stu-id="b3e67-158">This is done by calling the `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` helper method.</span></span>  
  
 <span data-ttu-id="b3e67-159">Ceci doit être fait avant d'appeler `CreateChannel`.</span><span class="sxs-lookup"><span data-stu-id="b3e67-159">This must be done before calling `CreateChannel`.</span></span>  
  
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
  
 <span data-ttu-id="b3e67-160">Sur le serveur :</span><span class="sxs-lookup"><span data-stu-id="b3e67-160">On the server:</span></span>  
  
- <span data-ttu-id="b3e67-161">L'interface <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> doit être implémentée afin qu'elle puisse lire les demandes HTTP GET et déléguer l'écriture des réponses au formateur d'origine.</span><span class="sxs-lookup"><span data-stu-id="b3e67-161">The <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interface must be implemented so that it can read HTTP GET requests and delegate to the original formatter for writing responses.</span></span> <span data-ttu-id="b3e67-162">Cela est effectué en appelant la même méthode d'assistance `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` que le client (consultez l'exemple de code précédent).</span><span class="sxs-lookup"><span data-stu-id="b3e67-162">This is done by calling the same `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` helper method as the client (see the previous code sample).</span></span>  
  
- <span data-ttu-id="b3e67-163">Ceci doit être fait avant d'appeler <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span><span class="sxs-lookup"><span data-stu-id="b3e67-163">This must be done before <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> is called.</span></span> <span data-ttu-id="b3e67-164">Dans cet exemple, nous montrons comment le formateur est modifié manuellement avant d'appeler <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span><span class="sxs-lookup"><span data-stu-id="b3e67-164">In this sample, we show how the formatter is manually modified before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span> <span data-ttu-id="b3e67-165">Pour parvenir au même résultat, il est possible de dériver une classe de <xref:System.ServiceModel.ServiceHost> qui appelle `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` avant de s'ouvrir (consultez la documentation et les exemples relatifs à l'hébergement).</span><span class="sxs-lookup"><span data-stu-id="b3e67-165">Another way to achieve the same thing is to derive a class from <xref:System.ServiceModel.ServiceHost> that makes the calls to `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` before opening (please see hosting documentation and samples for examples).</span></span>  
  
### <a name="user-experience"></a><span data-ttu-id="b3e67-166">Expérience utilisateur</span><span class="sxs-lookup"><span data-stu-id="b3e67-166">User experience</span></span>  
 <span data-ttu-id="b3e67-167">Sur le serveur :</span><span class="sxs-lookup"><span data-stu-id="b3e67-167">On the server:</span></span>  
  
- <span data-ttu-id="b3e67-168">L'implémentation serveur `ICalculator` n'a pas besoin d'être modifiée.</span><span class="sxs-lookup"><span data-stu-id="b3e67-168">The server `ICalculator` implementation does not need to change.</span></span>  
  
- <span data-ttu-id="b3e67-169">L’App.config pour le service doit utiliser une liaison POX personnalisée qui affecte à l’attribut `messageVersion` de l’élément `textMessageEncoding` la valeur `None`.</span><span class="sxs-lookup"><span data-stu-id="b3e67-169">The App.config for the service must use a custom POX binding that sets the `messageVersion` attribute of the `textMessageEncoding` element to `None`.</span></span>  
  
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
  
- <span data-ttu-id="b3e67-170">L’App.config pour le service doit également spécifier le `EnableHttpGetRequestsBehavior` personnalisé en l’ajoutant à la section d’extensions de comportement et en l’utilisant.</span><span class="sxs-lookup"><span data-stu-id="b3e67-170">The App.config for the service also must specify the custom `EnableHttpGetRequestsBehavior` by adding it to the behavior extensions section and using it.</span></span>  
  
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
  
- <span data-ttu-id="b3e67-171">Ajoutez les formateurs d'opération avant d'appeler <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span><span class="sxs-lookup"><span data-stu-id="b3e67-171">Add operation formatters before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span>  
  
 <span data-ttu-id="b3e67-172">Sur le client :</span><span class="sxs-lookup"><span data-stu-id="b3e67-172">On the client:</span></span>  
  
- <span data-ttu-id="b3e67-173">L'implémentation cliente  n'a pas besoin d'être modifiée.</span><span class="sxs-lookup"><span data-stu-id="b3e67-173">The client implementation does not need to change.</span></span>  
  
- <span data-ttu-id="b3e67-174">L’App.config pour le client doit utiliser une liaison POX personnalisée qui affecte à l’attribut `messageVersion` de l’élément `textMessageEncoding` la valeur `None`.</span><span class="sxs-lookup"><span data-stu-id="b3e67-174">The App.config for the client must use a custom POX binding that sets the `messageVersion` attribute of the `textMessageEncoding` element to `None`.</span></span> <span data-ttu-id="b3e67-175">À la différence du service, le client doit activer l'adressage manuel afin que l'adresse To sortante puisse être modifiée.</span><span class="sxs-lookup"><span data-stu-id="b3e67-175">One difference from the service is that the client must enable manual addressing so that the outgoing To address can be modified.</span></span>  
  
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
  
- <span data-ttu-id="b3e67-176">L'App.config pour le client doit spécifier le même `EnableHttpGetRequestsBehavior` personnalisé que le serveur.</span><span class="sxs-lookup"><span data-stu-id="b3e67-176">The App.config for the client must specify the same custom `EnableHttpGetRequestsBehavior` as the server.</span></span>  
  
- <span data-ttu-id="b3e67-177">Ajoutez les formateurs d'opération avant d'appeler <xref:System.ServiceModel.ChannelFactory%601.CreateChannel>.</span><span class="sxs-lookup"><span data-stu-id="b3e67-177">Add operation formatters before calling <xref:System.ServiceModel.ChannelFactory%601.CreateChannel>.</span></span>  
  
 <span data-ttu-id="b3e67-178">Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client.</span><span class="sxs-lookup"><span data-stu-id="b3e67-178">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="b3e67-179">Les quatre opérations (addition, soustraction, multiplication et division) doivent réussir.</span><span class="sxs-lookup"><span data-stu-id="b3e67-179">All four operations (Add, Subtract, Multiply, and Divide) must succeed.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b3e67-180">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b3e67-180">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b3e67-181">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="b3e67-181">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="b3e67-182">Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons.</span><span class="sxs-lookup"><span data-stu-id="b3e67-182">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b3e67-183">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="b3e67-183">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Formatters\QueryStringFormatter`  
  
##### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b3e67-184">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="b3e67-184">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="b3e67-185">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les échantillons de la Fondation De communication Windows.](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)</span><span class="sxs-lookup"><span data-stu-id="b3e67-185">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="b3e67-186">Pour construire la solution, suivez les instructions dans [la construction des échantillons de la Fondation De communication Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b3e67-186">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="b3e67-187">Pour exécuter l’échantillon dans une configuration mono-ou cross-machine, suivez les instructions dans [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b3e67-187">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
