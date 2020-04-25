---
title: Durable Instance Context
ms.date: 03/30/2017
ms.assetid: 97bc2994-5a2c-47c7-927a-c4cd273153df
ms.openlocfilehash: 604a617dc03bf06b71fe3019b58b2161216ee3e0
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141183"
---
# <a name="durable-instance-context"></a><span data-ttu-id="d3fa1-102">Durable Instance Context</span><span class="sxs-lookup"><span data-stu-id="d3fa1-102">Durable Instance Context</span></span>

<span data-ttu-id="d3fa1-103">Cet exemple montre comment personnaliser le runtime Windows Communication Foundation (WCF) pour activer des contextes d’instance durables.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-103">This sample demonstrates how to customize the Windows Communication Foundation (WCF) runtime to enable durable instance contexts.</span></span> <span data-ttu-id="d3fa1-104">Il utilise SQL Server 2005 comme magasin de sauvegarde (SQL Server 2005 Express dans ce cas précis).</span><span class="sxs-lookup"><span data-stu-id="d3fa1-104">It uses SQL Server 2005 as its backing store (SQL Server 2005 Express in this case).</span></span> <span data-ttu-id="d3fa1-105">Toutefois, il permet également d'accéder aux mécanismes de stockage personnalisés.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-105">However, it also provides a way to access custom storage mechanisms.</span></span>

> [!NOTE]
> <span data-ttu-id="d3fa1-106">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="d3fa1-107">Cet exemple implique l’extension de la couche de canal et de la couche de modèle de service de WCF.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-107">This sample involves extending both the channel layer and the service model layer of the WCF.</span></span> <span data-ttu-id="d3fa1-108">Par conséquent, il est nécessaire de comprendre les concepts sous-jacents avant d'aborder les détails de l'implémentation.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-108">Therefore it is necessary to understand the underlying concepts before going into the implementation details.</span></span>

<span data-ttu-id="d3fa1-109">Les contextes d'instance fiables se trouvent souvent dans des scénarios réels.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-109">Durable instance contexts can be found in the real world scenarios quite often.</span></span> <span data-ttu-id="d3fa1-110">Une application de panier d'achat par exemple, permet de suspendre le processus d'achat et de le poursuivre ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-110">A shopping cart application for example, has the ability to pause shopping halfway through and continue it on another day.</span></span> <span data-ttu-id="d3fa1-111">De cette façon, lorsque nous visitons le panier d'achat le jour suivant, le contexte d'origine est restauré.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-111">So that when we visit the shopping cart the next day, our original context is restored.</span></span> <span data-ttu-id="d3fa1-112">Il est important de noter que l'application de panier d'achat (sur le serveur) ne conserve pas l'instance correspondante en cas de déconnexion.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-112">It is important to note that the shopping cart application (on the server) does not maintain the shopping cart instance while we are disconnected.</span></span> <span data-ttu-id="d3fa1-113">À la place, elle rend son état persistant dans un média de stockage fiable et l'utilise lors de la construction d'une nouvelle instance pour le contexte restauré.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-113">Instead, it persists its state into a durable storage media and uses it when constructing a new instance for the restored context.</span></span> <span data-ttu-id="d3fa1-114">Par conséquent l'instance de service qui peut servir pour le même contexte n'est pas la même que l'instance précédente (autrement dit, elle n'a pas la même adresse mémoire).</span><span class="sxs-lookup"><span data-stu-id="d3fa1-114">Therefore the service instance that may service for the same context is not the same as the previous instance (that is, it does not have the same memory address).</span></span>

<span data-ttu-id="d3fa1-115">Le contexte d'instance fiable est rendu possible par un petit protocole qui échange un ID de contexte entre le client et le service.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-115">Durable instance context is made possible by a small protocol that exchanges a context ID between the client and service.</span></span> <span data-ttu-id="d3fa1-116">Cet ID de contexte est créé sur le client et est transmis au service.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-116">This context ID is created on the client and transmitted to the service.</span></span> <span data-ttu-id="d3fa1-117">Lorsque l'instance de service est créée, l'exécution du service essaie de charger l'état persistant qui correspond à cet ID de contexte à partir d'un stockage persistant (par défaut, il s'agit d'une base de données SQL Server 2005).</span><span class="sxs-lookup"><span data-stu-id="d3fa1-117">When the service instance is created, the service runtime tries to load the persisted state that corresponds to this context ID from a persistent storage (by default it is a SQL Server 2005 database).</span></span> <span data-ttu-id="d3fa1-118">Si aucun état n'est disponible, la nouvelle instance a son état par défaut.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-118">If no state is available the new instance has its default state.</span></span> <span data-ttu-id="d3fa1-119">L'implémentation de service utilise un attribut personnalisé pour marquer les opérations qui modifient l'état de l'implémentation de service afin que l'exécution puisse enregistrer l'instance de service après les avoir appelées.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-119">The service implementation uses a custom attribute to mark operations that change the state of the service implementation so that the runtime can save the service instance after invoking them.</span></span>

<span data-ttu-id="d3fa1-120">Dans la description précédente, on distingue clairement deux étapes permettant d'atteindre cet objectif :</span><span class="sxs-lookup"><span data-stu-id="d3fa1-120">By the previous description, two steps can easily be distinguished to achieve the goal:</span></span>

1. <span data-ttu-id="d3fa1-121">Modification du message sur le câble afin de transmettre l'ID de contexte.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-121">Change the message that goes on the wire to carry the context ID.</span></span>

2. <span data-ttu-id="d3fa1-122">Modification du comportement local du service afin d'implémenter la logique d'instanciation personnalisée.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-122">Change the service local behavior to implement custom instancing logic.</span></span>

<span data-ttu-id="d3fa1-123">La première étape mentionnée affectant les messages sur le câble, elle doit être implémentée sous forme d'un canal personnalisé et être raccordée à la couche de canal.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-123">Because the first one in the list affects the messages on the wire it should be implemented as a custom channel and be hooked up to the channel layer.</span></span> <span data-ttu-id="d3fa1-124">La dernière affecte uniquement le comportement local du service et peut par conséquent être implémentée en étendant plusieurs points d'extensibilité.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-124">The latter only affects the service local behavior and therefore can be implemented by extending several service extensibility points.</span></span> <span data-ttu-id="d3fa1-125">Chacune des extensions suivantes est traitée dans les sections ci-après.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-125">In the next few sections, each of these extensions are discussed.</span></span>

## <a name="durable-instancecontext-channel"></a><span data-ttu-id="d3fa1-126">Canal InstanceContext fiable</span><span class="sxs-lookup"><span data-stu-id="d3fa1-126">Durable InstanceContext Channel</span></span>

<span data-ttu-id="d3fa1-127">La première chose à examiner est une extension de la couche de canal.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-127">The first thing to look at is a channel layer extension.</span></span> <span data-ttu-id="d3fa1-128">La première étape de l'écriture d'un canal personnalisé consiste à déterminer la structure de communication du canal.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-128">The first step in writing a custom channel is to decide the communication structure of the channel.</span></span> <span data-ttu-id="d3fa1-129">Un nouveau protocole de câble étant introduit, le canal doit fonctionner avec la quasi-totalité des autres canaux de la pile.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-129">As a new wire protocol is being introduced the channel should work with almost any other channel in the channel stack.</span></span> <span data-ttu-id="d3fa1-130">Par conséquent, il doit prendre en charge l’ensemble des modèles d’échange de messages.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-130">Therefore it should support all the message exchange patterns.</span></span> <span data-ttu-id="d3fa1-131">Toutefois, la fonctionnalité principale du canal est la même, quelle que soit sa structure de communication.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-131">However, the core functionality of the channel is the same regardless of its communication structure.</span></span> <span data-ttu-id="d3fa1-132">Plus précisément, du côté client il doit écrire l'ID de contexte dans les messages, et du côté service il doit lire cet ID de contexte à partir des messages et le passer aux niveaux supérieurs.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-132">More specifically, from the client it should write the context ID to the messages and from the service it should read this context ID from the messages and pass it to the upper levels.</span></span> <span data-ttu-id="d3fa1-133">De ce fait, une classe `DurableInstanceContextChannelBase` est créée et agit en tant que classe de base abstraite pour toutes les implémentations de canal de contexte d'instance fiable.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-133">Because of that, a `DurableInstanceContextChannelBase` class is created that acts as the abstract base class for all durable instance context channel implementations.</span></span> <span data-ttu-id="d3fa1-134">Cette classe contient les fonctions de gestion de machine d'état courantes ainsi que deux membres protégés afin d'appliquer et de lire les informations de contexte vers et à partir des messages.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-134">This class contains the common state machine management functions and two protected members to apply and read the context information to and from messages.</span></span>

```csharp
class DurableInstanceContextChannelBase
{
  //…
  protected void ApplyContext(Message message)
  {
    //…
  }
  protected string ReadContextId(Message message)
  {
    //…
  }
}
```

<span data-ttu-id="d3fa1-135">Ces deux méthodes utilisent des implémentations `IContextManager` pour écrire et lire l'ID de contexte vers ou à partir du message </span><span class="sxs-lookup"><span data-stu-id="d3fa1-135">These two methods make use of `IContextManager` implementations to write and read the context ID to or from the message.</span></span> <span data-ttu-id="d3fa1-136">(`IContextManager` est une interface personnalisée utilisée pour définir le contrat pour tous les gestionnaires de contexte.) Le canal peut inclure l’ID de contexte dans un en-tête SOAP personnalisé ou dans un en-tête de cookie HTTP.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-136">(`IContextManager` is a custom interface used to define the contract for all context managers.) The channel can either include the context ID in a custom SOAP header or in a HTTP cookie header.</span></span> <span data-ttu-id="d3fa1-137">Chaque implémentation de gestionnaire de contexte hérite de la classe `ContextManagerBase` qui contient les fonctionnalités communes de tous les gestionnaires de contexte.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-137">Each context manager implementation inherits from the `ContextManagerBase` class that contains the common functionality for all context managers.</span></span> <span data-ttu-id="d3fa1-138">La méthode `GetContextId` de cette classe permet de générer l'ID de contexte à partir du client.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-138">The `GetContextId` method in this class is used to originate the context ID from the client.</span></span> <span data-ttu-id="d3fa1-139">Lorsqu'un ID de contexte est généré pour la première fois, cette méthode l'enregistre dans un fichier texte dont le nom est construit par l'adresse du point de terminaison distant (les caractères de nom de fichier non valides dans les URI classiques sont remplacés par des caractères @).</span><span class="sxs-lookup"><span data-stu-id="d3fa1-139">When a context ID is originated for the first time, this method saves it into a text file whose name is constructed by the remote endpoint address (the invalid file name characters in the typical URIs are replaced with @ characters).</span></span>

<span data-ttu-id="d3fa1-140">Par la suite, lorsque l'ID de contexte est requis pour le même point de terminaison distant, il vérifie si un fichier approprié existe.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-140">Later when the context ID is required for the same remote endpoint, it checks whether an appropriate file exists.</span></span> <span data-ttu-id="d3fa1-141">Si c'est le cas, il lit l'ID de contexte et retourne.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-141">If it does, it reads the context ID and returns.</span></span> <span data-ttu-id="d3fa1-142">Sinon, il retourne un ID de contexte généré récemment et l'enregistre dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-142">Otherwise it returns a newly generated context ID and saves it to a file.</span></span> <span data-ttu-id="d3fa1-143">Avec la configuration par défaut, ces fichiers sont placés dans un répertoire appelé ContextStore, qui réside dans le répertoire temporaire de l'utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-143">With the default configuration, these files are placed in a directory called ContextStore, which resides in the current user’s temp directory.</span></span> <span data-ttu-id="d3fa1-144">Toutefois, cet emplacement est configurable à l’aide de l’élément de liaison.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-144">However this location is configurable using the binding element.</span></span>

<span data-ttu-id="d3fa1-145">Le mécanisme utilisé pour transporter l'ID de contexte est configurable.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-145">The mechanism used to transport the context ID is configurable.</span></span> <span data-ttu-id="d3fa1-146">Il peut être écrit dans l'en-tête cookie HTTP ou dans un en-tête SOAP personnalisé.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-146">It could be either written to the HTTP cookie header or to a custom SOAP header.</span></span> <span data-ttu-id="d3fa1-147">L'approche utilisant l'en-tête SOAP personnalisé permet d'utiliser ce protocole avec des protocoles non HTTP (par exemple, TCP ou canaux nommés).</span><span class="sxs-lookup"><span data-stu-id="d3fa1-147">The custom SOAP header approach makes it possible to use this protocol with non-HTTP protocols (for example, TCP or Named Pipes).</span></span> <span data-ttu-id="d3fa1-148">Les deux classes `MessageHeaderContextManager` et `HttpCookieContextManager` implémentent ces deux options.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-148">There are two classes, namely `MessageHeaderContextManager` and `HttpCookieContextManager`, which implement these two options.</span></span>

<span data-ttu-id="d3fa1-149">Elles écrivent l'ID de contexte dans le message de manière appropriée.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-149">Both of them write the context ID to the message appropriately.</span></span> <span data-ttu-id="d3fa1-150">Par exemple, la classe `MessageHeaderContextManager` l'écrit dans un en-tête SOAP de la méthode `WriteContext`.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-150">For example, the `MessageHeaderContextManager` class writes it to a SOAP header in the `WriteContext` method.</span></span>

```csharp
public override void WriteContext(Message message)
{
  string contextId = this.GetContextId();

  MessageHeader contextHeader =
    MessageHeader.CreateHeader(DurableInstanceContextUtility.HeaderName,
      DurableInstanceContextUtility.HeaderNamespace,
      contextId,
      true);

  message.Headers.Add(contextHeader);
}
```

<span data-ttu-id="d3fa1-151">Les méthodes `ApplyContext` et `ReadContextId` de la classe `DurableInstanceContextChannelBase` appellent `IContextManager.ReadContext` et `IContextManager.WriteContext`, respectivement.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-151">Both the `ApplyContext` and `ReadContextId` methods in the `DurableInstanceContextChannelBase` class invoke the `IContextManager.ReadContext` and `IContextManager.WriteContext`, respectively.</span></span> <span data-ttu-id="d3fa1-152">Toutefois, ces gestionnaires de contexte ne sont pas directement créés par la classe `DurableInstanceContextChannelBase`.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-152">However, these context managers are not directly created by the `DurableInstanceContextChannelBase` class.</span></span> <span data-ttu-id="d3fa1-153">Cette tâche est accomplie par la classe `ContextManagerFactory`.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-153">Instead it uses the `ContextManagerFactory` class to do that job.</span></span>

```csharp
IContextManager contextManager =
                ContextManagerFactory.CreateContextManager(contextType,
                this.contextStoreLocation,
                this.endpointAddress);
```

<span data-ttu-id="d3fa1-154">La méthode `ApplyContext` est appelée par les canaux d'envoi.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-154">The `ApplyContext` method is invoked by the sending channels.</span></span> <span data-ttu-id="d3fa1-155">Elle injecte l'ID de contexte dans les messages sortants.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-155">It injects the context ID to the outgoing messages.</span></span> <span data-ttu-id="d3fa1-156">La méthode `ReadContextId` est appelée par les canaux de réception.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-156">The `ReadContextId` method is invoked by the receiving channels.</span></span> <span data-ttu-id="d3fa1-157">Cette méthode garantit que l’ID de contexte est disponible dans les messages entrants et l’ajoute à la collection `Properties` de la classe `Message`.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-157">This method ensures that the context ID is available in the incoming messages and adds it to the `Properties` collection of the `Message` class.</span></span> <span data-ttu-id="d3fa1-158">Elle lève également une exception `CommunicationException` en cas d'échec de lecture de l'ID de contexte et provoque donc l'abandon du canal.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-158">It also throws a `CommunicationException` in case of a failure to read the context ID and thus causes the channel to be aborted.</span></span>

```csharp
message.Properties.Add(DurableInstanceContextUtility.ContextIdProperty, contextId);
```

<span data-ttu-id="d3fa1-159">Avant de poursuivre, il est important de comprendre l’utilisation de la collection `Properties` dans la classe `Message`.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-159">Before proceeding, it is important to understand the usage of the `Properties` collection in the `Message` class.</span></span> <span data-ttu-id="d3fa1-160">En général, cette collection `Properties` est utilisée lors du passage des données des niveaux inférieurs aux niveaux supérieurs de la couche de canal.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-160">Typically, this `Properties` collection is used when passing data from lower to the upper levels from the channel layer.</span></span> <span data-ttu-id="d3fa1-161">De cette manière, les données souhaitées peuvent être fournies aux niveaux supérieurs de façon cohérente, quels que soient les détails du protocole.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-161">This way the desired data can be provided to the upper levels in a consistent manner regardless of the protocol details.</span></span> <span data-ttu-id="d3fa1-162">En d'autres termes, la couche de canal peut envoyer et recevoir l'ID de contexte sous forme d'un en-tête SOAP ou d'un en-tête cookie HTTP.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-162">In other words, the channel layer can send and receive the context ID either as a SOAP header or a HTTP cookie header.</span></span> <span data-ttu-id="d3fa1-163">Mais il n’est pas nécessaire que les niveaux supérieurs connaissent ces détails car la couche de canal rend ces informations disponibles dans la collection `Properties`.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-163">But it is not necessary for the upper levels to know about these details because the channel layer makes this information available in the `Properties` collection.</span></span>

<span data-ttu-id="d3fa1-164">La classe `DurableInstanceContextChannelBase` étant maintenant en place, l'ensemble des dix interfaces nécessaires (IOutputChannel, IInputChannel, IOutputSessionChannel, IInputSessionChannel, IRequestChannel, IReplyChannel, IRequestSessionChannel, IReplySessionChannel, IDuplexChannel, IDuplexSessionChannel) doivent être implémentées.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-164">Now with the `DurableInstanceContextChannelBase` class in place all ten of the necessary interfaces (IOutputChannel, IInputChannel, IOutputSessionChannel, IInputSessionChannel, IRequestChannel, IReplyChannel, IRequestSessionChannel, IReplySessionChannel, IDuplexChannel, IDuplexSessionChannel) must be implemented.</span></span> <span data-ttu-id="d3fa1-165">Elles ressemblent à chaque modèle d’échange de messages disponible (datagramme, simplex, duplex et leurs variantes de session).</span><span class="sxs-lookup"><span data-stu-id="d3fa1-165">They resemble every available message exchange pattern (datagram, simplex, duplex and their sessionful variants).</span></span> <span data-ttu-id="d3fa1-166">Chacune de ces implémentations hérite de la classe de base précédemment décrite et appelle `ApplyContext` et `ReadContextId` de manière appropriée.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-166">Each of these implementations inherit the base class previously described and calls `ApplyContext` and `ReadContextId` appropriately.</span></span> <span data-ttu-id="d3fa1-167">Par exemple, `DurableInstanceContextOutputChannel`, qui implémente l'interface IOutputChannel, appelle la méthode `ApplyContext` de chaque méthode qui envoie les messages.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-167">For example, `DurableInstanceContextOutputChannel` - which implements the IOutputChannel interface - calls the `ApplyContext` method from each method that sends the messages.</span></span>

```csharp
public void Send(Message message, TimeSpan timeout)
{
    // Apply the context information before sending the message.
    this.ApplyContext(message);
    //…
}
```

<span data-ttu-id="d3fa1-168">En revanche, `DurableInstanceContextInputChannel`, qui implémente l'interface `IInputChannel`, appelle la méthode `ReadContextId` de chaque méthode qui reçoit les messages.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-168">On the other hand, `DurableInstanceContextInputChannel` - which implements the `IInputChannel` interface - calls the `ReadContextId` method in each method which receives the messages.</span></span>

```csharp
public Message Receive(TimeSpan timeout)
{
    //…
      ReadContextId(message);
      return message;
}
```

<span data-ttu-id="d3fa1-169">En outre, ces implémentations de canal délèguent les appels de méthode au canal inférieur dans la pile de canaux.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-169">Apart from this, these channel implementations delegate the method invocations to the channel below them in the channel stack.</span></span> <span data-ttu-id="d3fa1-170">Toutefois, les variantes de session ont une logique de base permettant de s'assurer que l'ID de contexte est envoyé et est lu uniquement pour le premier message qui provoque la création de la session.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-170">However, sessionful variants have a basic logic to make sure that the context ID is sent and is read only for the first message that causes the session to be created.</span></span>

```csharp
if (isFirstMessage)
{
//…
    this.ApplyContext(message);
    isFirstMessage = false;
}
```

<span data-ttu-id="d3fa1-171">Ces implémentations de canal sont ensuite ajoutées au runtime du canal WCF par `DurableInstanceContextBindingElement` la classe `DurableInstanceContextBindingElementSection` et la classe de manière appropriée.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-171">These channel implementations are then added to the WCF channel runtime by the `DurableInstanceContextBindingElement` class and `DurableInstanceContextBindingElementSection` class appropriately.</span></span> <span data-ttu-id="d3fa1-172">Consultez la documentation de l’exemple de canal [HttpCookieSession](../../../../docs/framework/wcf/samples/httpcookiesession.md) pour plus d’informations sur les éléments de liaison et les sections d’éléments de liaison.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-172">See the [HttpCookieSession](../../../../docs/framework/wcf/samples/httpcookiesession.md) channel sample documentation for more details about binding elements and binding element sections.</span></span>

## <a name="service-model-layer-extensions"></a><span data-ttu-id="d3fa1-173">Extensions de la couche de modèle de service</span><span class="sxs-lookup"><span data-stu-id="d3fa1-173">Service Model Layer Extensions</span></span>

<span data-ttu-id="d3fa1-174">Maintenant que l'ID de contexte a traversé la couche de canal, le comportement de service peut être implémenté afin de personnaliser l'instanciation.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-174">Now that the context ID has traveled through the channel layer, the service behavior can be implemented to customize the instantiation.</span></span> <span data-ttu-id="d3fa1-175">Dans cet exemple, un gestionnaire de stockage est utilisé pour charger et enregistrer l'état à partir de ou vers le magasin persistant.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-175">In this sample, a storage manager is used to load and save state from or to the persistent store.</span></span> <span data-ttu-id="d3fa1-176">Comme expliqué précédemment, cet exemple fournit un gestionnaire de stockage qui utilise le SQL Server 2005 comme magasin de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-176">As explained previously, this sample provides a storage manager that uses SQL Server 2005 as its backing store.</span></span> <span data-ttu-id="d3fa1-177">Toutefois, il est également possible d’ajouter des mécanismes de stockage personnalisés à cette extension.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-177">However, it is also possible to add custom storage mechanisms to this extension.</span></span> <span data-ttu-id="d3fa1-178">Pour ce faire, une interface publique est déclarée et doit être implémentée par tous les gestionnaires de stockage.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-178">To do that a public interface is declared, which must be implemented by all storage managers.</span></span>

```csharp
public interface IStorageManager
{
    object GetInstance(string contextId, Type type);
    void SaveInstance(string contextId, object state);
}
```

<span data-ttu-id="d3fa1-179">La classe `SqlServerStorageManager` contient l'implémentation `IStorageManager` par défaut.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-179">The `SqlServerStorageManager` class contains the default `IStorageManager` implementation.</span></span> <span data-ttu-id="d3fa1-180">Dans sa méthode `SaveInstance`, l'objet donné est sérialisé à l'aide de XmlSerializer et est enregistré dans la base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-180">In its `SaveInstance` method the given object is serialized using the XmlSerializer and is saved to the SQL Server database.</span></span>

```csharp
XmlSerializer serializer = new XmlSerializer(state.GetType());
string data;

using (StringWriter writer = new StringWriter(CultureInfo.InvariantCulture))
{
    serializer.Serialize(writer, state);
    data = writer.ToString();
}

using (SqlConnection connection = new SqlConnection(GetConnectionString()))
{
    connection.Open();

    string update = @"UPDATE Instances SET Instance = @instance WHERE ContextId = @contextId";

    using (SqlCommand command = new SqlCommand(update, connection))
    {
        command.Parameters.Add("@instance", SqlDbType.VarChar, 2147483647).Value = data;
        command.Parameters.Add("@contextId", SqlDbType.VarChar, 256).Value = contextId;

        int rows = command.ExecuteNonQuery();

        if (rows == 0)
        {
            string insert = @"INSERT INTO Instances(ContextId, Instance) VALUES(@contextId, @instance)";
            command.CommandText = insert;
            command.ExecuteNonQuery();
        }
    }
}
```

<span data-ttu-id="d3fa1-181">Dans la méthode `GetInstance`, les données sérialisées sont lues pour un ID de contexte donné, et l'objet construit à partir de celui-ci est retourné à l'appelant.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-181">In the `GetInstance` method the serialized data is read for a given context ID and the object constructed from it is returned to the caller.</span></span>

```csharp
object data;
using (SqlConnection connection = new SqlConnection(GetConnectionString()))
{
    connection.Open();

    string select = "SELECT Instance FROM Instances WHERE ContextId = @contextId";
    using (SqlCommand command = new SqlCommand(select, connection))
    {
        command.Parameters.Add("@contextId", SqlDbType.VarChar, 256).Value = contextId;
        data = command.ExecuteScalar();
    }
}

if (data != null)
{
    XmlSerializer serializer = new XmlSerializer(type);
    using (StringReader reader = new StringReader((string)data))
    {
        object instance = serializer.Deserialize(reader);
        return instance;
    }
}
```

<span data-ttu-id="d3fa1-182">Les utilisateurs de ces gestionnaires de stockage ne sont pas supposés les instancier directement.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-182">Users of these storage managers are not supposed to instantiate them directly.</span></span> <span data-ttu-id="d3fa1-183">Ils utilisent la classe `StorageManagerFactory`, qui abstrait à partir des détails de création de gestionnaire de stockage.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-183">They use the `StorageManagerFactory` class, which abstracts from the storage manager creation details.</span></span> <span data-ttu-id="d3fa1-184">Cette classe possède le membre statique `GetStorageManager` qui crée une instance d'un type de gestionnaire de stockage donné.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-184">This class has one static member, `GetStorageManager`, which creates an instance of a given storage manager type.</span></span> <span data-ttu-id="d3fa1-185">Si le paramètre de type est `null`, cette méthode crée une instance de la classe `SqlServerStorageManager` par défaut et la retourne.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-185">If the type parameter is `null`, this method creates an instance of the default `SqlServerStorageManager` class and returns it.</span></span> <span data-ttu-id="d3fa1-186">Elle valide également le type donné afin de s'assurer qu'il implémente l'interface `IStorageManager`.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-186">It also validates the given type to make sure that it implements the `IStorageManager` interface.</span></span>

```csharp
public static IStorageManager GetStorageManager(Type storageManagerType)
{
IStorageManager storageManager = null;

if (storageManagerType == null)
{
    return new SqlServerStorageManager();
}
else
{
    object obj = Activator.CreateInstance(storageManagerType);

    // Throw if the specified storage manager type does not
    // implement IStorageManager.
    if (obj is IStorageManager)
    {
        storageManager = (IStorageManager)obj;
    }
    else
    {
        throw new InvalidOperationException(
                  ResourceHelper.GetString("ExInvalidStorageManager"));
    }

    return storageManager;
}
}
```

<span data-ttu-id="d3fa1-187">L'infrastructure nécessaire pour lire et écrire des instances à partir du stockage persistant est implémentée.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-187">The necessary infrastructure to read and write instances from the persistent storage is implemented.</span></span> <span data-ttu-id="d3fa1-188">Les étapes nécessaires pour modifier le comportement de service doivent maintenant être effectuées.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-188">Now the necessary steps to change the service behavior have to be taken.</span></span>

<span data-ttu-id="d3fa1-189">La première étape de ce processus consiste à enregistrer l'ID de contexte, qui a traversé la couche de canal jusqu'au InstanceContext actuel.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-189">As the first step of this process we have to save the context ID, which came through the channel layer to the current InstanceContext.</span></span> <span data-ttu-id="d3fa1-190">InstanceContext est un composant d’exécution qui agit comme lien entre le répartiteur WCF et l’instance de service.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-190">InstanceContext is a runtime component that acts as the link between the WCF dispatcher and the service instance.</span></span> <span data-ttu-id="d3fa1-191">Il permet de fournir un comportement et un état supplémentaires à l'instance de service.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-191">It can be used to provide additional state and behavior to the service instance.</span></span> <span data-ttu-id="d3fa1-192">Cet aspect est essentiel car dans la communication de session, l'ID de contexte est envoyé uniquement avec le premier message.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-192">This is essential because in sessionful communication the context ID is sent only with the first message.</span></span>

<span data-ttu-id="d3fa1-193">WCF permet d’étendre son composant d’exécution InstanceContext en ajoutant un nouvel État et un nouveau comportement à l’aide de son modèle d’objet extensible.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-193">WCF allows extending its InstanceContext runtime component by adding a new state and behavior using its extensible object pattern.</span></span> <span data-ttu-id="d3fa1-194">Le modèle d’objet extensible est utilisé dans WCF pour étendre des classes d’exécution existantes avec de nouvelles fonctionnalités ou pour ajouter de nouvelles fonctionnalités d’État à un objet.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-194">The extensible object pattern is used in WCF to either extend existing runtime classes with new functionality or to add new state features to an object.</span></span> <span data-ttu-id="d3fa1-195">Il existe trois interfaces dans le modèle d’objet extensible-\<IExtensibleObject t>,\<IExtension t> et IExtensionCollection\<t> :</span><span class="sxs-lookup"><span data-stu-id="d3fa1-195">There are three interfaces in the extensible object pattern - IExtensibleObject\<T>, IExtension\<T>, and IExtensionCollection\<T>:</span></span>

- <span data-ttu-id="d3fa1-196">L’interface\<IExtensibleObject T> est implémentée par des objets qui autorisent les extensions qui personnalisent leurs fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-196">The IExtensibleObject\<T> interface is implemented by objects that allow extensions that customize their functionality.</span></span>

- <span data-ttu-id="d3fa1-197">L’interface\<IExtension T> est implémentée par des objets qui sont des extensions de classes de type T.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-197">The IExtension\<T> interface is implemented by objects that are extensions of classes of type T.</span></span>

- <span data-ttu-id="d3fa1-198">L’interface\<IExtensionCollection T> est une collection de IExtensions qui permet de récupérer des IExtensions à l’aide de leur type.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-198">The IExtensionCollection\<T> interface is a collection of IExtensions that allows for retrieving IExtensions by their type.</span></span>

<span data-ttu-id="d3fa1-199">Par conséquent, vous devez créer une classe InstanceContextExtension qui implémente l'interface IExtension et définit l'état requis pour enregistrer l'ID de contexte.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-199">Therefore an InstanceContextExtension class should be created that implements the IExtension interface and defines the required state to save the context ID.</span></span> <span data-ttu-id="d3fa1-200">Cette classe fournit également l'état permettant de conserver le gestionnaire de stockage utilisé.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-200">This class also provides the state to hold the storage manager being used.</span></span> <span data-ttu-id="d3fa1-201">Une fois que le nouvel état est enregistré, il ne doit pas être possible de le modifier.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-201">Once the new state is saved, it should not be possible to modify it.</span></span> <span data-ttu-id="d3fa1-202">L'état est donc fourni et enregistré dans l'instance au moment de sa construction et n'est ensuite accessible qu'en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-202">Therefore the state is provided and saved to the instance at the time it is being constructed and then only accessible using read-only properties.</span></span>

```csharp
// Constructor
public DurableInstanceContextExtension(string contextId,
            IStorageManager storageManager)
{
    this.contextId = contextId;
    this.storageManager = storageManager;
}

// Read only properties
public string ContextId
{
    get { return this.contextId; }
}

public IStorageManager StorageManager
{
    get { return this.storageManager; }
}
```

<span data-ttu-id="d3fa1-203">La classe InstanceContextInitializer implémente l'interface IInstanceContextInitializer et ajoute l'extension de contexte d'instance à la collection Extensions du InstanceContext en cours de construction.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-203">The InstanceContextInitializer class implements the IInstanceContextInitializer interface and adds the instance context extension to the Extensions collection of the InstanceContext being constructed.</span></span>

```csharp
public void Initialize(InstanceContext instanceContext, Message message)
{
    string contextId =
  (string)message.Properties[DurableInstanceContextUtility.ContextIdProperty];

    DurableInstanceContextExtension extension =
                new DurableInstanceContextExtension(contextId,
                     storageManager);
    instanceContext.Extensions.Add(extension);
}
```

<span data-ttu-id="d3fa1-204">Comme décrit précédemment, l'ID de contexte est lu à partir de la collection `Properties` de la classe `Message`, puis il est passé au constructeur de la classe d'extension.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-204">As described earlier the context ID is read from the `Properties` collection of the `Message` class and passed to the constructor of the extension class.</span></span> <span data-ttu-id="d3fa1-205">Cette étape montre comment les informations peuvent être échangées entre les couches de façon cohérente.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-205">This demonstrates how information can be exchanged between the layers in a consistent manner.</span></span>

<span data-ttu-id="d3fa1-206">L'étape importante suivante consiste à substituer le processus de création d'instance de service.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-206">The next important step is overriding the service instance creation process.</span></span> <span data-ttu-id="d3fa1-207">WCF permet d’implémenter des comportements d’instanciation personnalisés et de les raccorder au runtime à l’aide de l’interface IInstanceProvider.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-207">WCF allows implementing custom instantiation behaviors and hooking them up to the runtime using the IInstanceProvider interface.</span></span> <span data-ttu-id="d3fa1-208">Pour ce faire, la nouvelle classe `InstanceProvider` est implémentée.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-208">The new `InstanceProvider` class is implemented to do that job.</span></span> <span data-ttu-id="d3fa1-209">Dans le constructeur, le type de service attendu du fournisseur d'instances est accepté.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-209">In the constructor the service type expected from the instance provider is accepted.</span></span> <span data-ttu-id="d3fa1-210">Il est par la suite utilisé pour créer des instances.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-210">Later this is used to create new instances.</span></span> <span data-ttu-id="d3fa1-211">Dans l'implémentation `GetInstance`, une instance d'un gestionnaire de stockage est créée afin de rechercher une instance persistante.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-211">In the `GetInstance` implementation an instance of a storage manager is created looking for a persisted instance.</span></span> <span data-ttu-id="d3fa1-212">Si elle retourne `null`, une nouvelle instance du type de service est instanciée et retournée à l'appelant.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-212">If it returns `null` then a new instance of the service type is instantiated and returned to the caller.</span></span>

```csharp
public object GetInstance(InstanceContext instanceContext, Message message)
{
    object instance = null;

    DurableInstanceContextExtension extension =
    instanceContext.Extensions.Find<DurableInstanceContextExtension>();

    string contextId = extension.ContextId;
    IStorageManager storageManager = extension.StorageManager;

    instance = storageManager.GetInstance(contextId, serviceType);

    instance ??= Activator.CreateInstance(serviceType);
    return instance;
}
```

<span data-ttu-id="d3fa1-213">L'étape importante suivante consiste à  installer les classes `InstanceContextExtension`, `InstanceContextInitializer` et `InstanceProvider` dans l'exécution de modèle de service.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-213">The next important step is to install the `InstanceContextExtension`, `InstanceContextInitializer` and `InstanceProvider` classes into the service model runtime.</span></span> <span data-ttu-id="d3fa1-214">Un attribut personnalisé peut être utilisé pour marquer les classes d'implémentation de service afin d'installer le comportement.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-214">A custom attribute could be used to mark the service implementation classes to install the behavior.</span></span> <span data-ttu-id="d3fa1-215">`DurableInstanceContextAttribute` contient l'implémentation pour cet attribut et implémente l'interface `IServiceBehavior` afin d'étendre l'ensemble de l'exécution du service.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-215">The `DurableInstanceContextAttribute` contains the implementation for this attribute and it implements the `IServiceBehavior` interface to extend the entire service runtime.</span></span>

<span data-ttu-id="d3fa1-216">Cette classe possède une propriété qui accepte le type du gestionnaire de stockage à utiliser.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-216">This class has a property that accepts the type of the storage manager to be used.</span></span> <span data-ttu-id="d3fa1-217">De cette manière, l'implémentation permet aux utilisateurs de spécifier leur propre implémentation `IStorageManager` comme paramètre de cet attribut.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-217">In this way the implementation enables the users to specify their own `IStorageManager` implementation as parameter of this attribute.</span></span>

<span data-ttu-id="d3fa1-218">Dans l'implémentation `ApplyDispatchBehavior`, le `InstanceContextMode` de l'attribut `ServiceBehavior` actuel est vérifié.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-218">In the `ApplyDispatchBehavior` implementation the `InstanceContextMode` of the current `ServiceBehavior` attribute is being verified.</span></span> <span data-ttu-id="d3fa1-219">Si cette propriété a pour valeur Singleton, l'activation de l'instanciation fiable n'est pas possible et une exception `InvalidOperationException` est levée pour notifier l'hôte.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-219">If this property is set to Singleton, enabling durable instancing is not possible and an `InvalidOperationException` is thrown to notify the host.</span></span>

```csharp
ServiceBehaviorAttribute serviceBehavior =
    serviceDescription.Behaviors.Find<ServiceBehaviorAttribute>();

if (serviceBehavior != null &&
     serviceBehavior.InstanceContextMode == InstanceContextMode.Single)
{
    throw new InvalidOperationException(
       ResourceHelper.GetString("ExSingletonInstancingNotSupported"));
}
```

<span data-ttu-id="d3fa1-220">Puis les instances du gestionnaire de stockage, l'initialiseur de contexte d'instance et le fournisseur d'instances sont créés et installés dans le `DispatchRuntime` créé pour chaque point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-220">After this the instances of the storage manager, instance context initializer, and the instance provider are created and installed in the `DispatchRuntime` created for every endpoint.</span></span>

```csharp
IStorageManager storageManager =
    StorageManagerFactory.GetStorageManager(storageManagerType);

InstanceContextInitializer contextInitializer =
    new InstanceContextInitializer(storageManager);

InstanceProvider instanceProvider =
    new InstanceProvider(description.ServiceType);

foreach (ChannelDispatcherBase cdb in serviceHostBase.ChannelDispatchers)
{
    ChannelDispatcher cd = cdb as ChannelDispatcher;

    if (cd != null)
    {
        foreach (EndpointDispatcher ed in cd.Endpoints)
        {
            ed.DispatchRuntime.InstanceContextInitializers.Add(contextInitializer);
            ed.DispatchRuntime.InstanceProvider = instanceProvider;
        }
    }
}
```

<span data-ttu-id="d3fa1-221">En résumé des étapes effectuées jusqu'à présent, cet exemple a produit un canal qui a activé le protocole de câble personnalisé pour l'échange d'ID de contexte personnalisé et il remplace également le comportement d'instanciation par défaut afin de charger les instances à partir du stockage persistant.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-221">In summary so far, this sample has produced a channel that enabled the custom wire protocol for custom context ID exchange and it also overwrites the default instancing behavior to load the instances from the persistent storage.</span></span>

<span data-ttu-id="d3fa1-222">Il reste donc à enregistrer l'instance de service dans le stockage persistant.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-222">What is left is a way to save the service instance to the persistent storage.</span></span> <span data-ttu-id="d3fa1-223">Comme indiqué précédemment, les fonctionnalités requises pour enregistrer l'état dans une implémentation `IStorageManager` existent déjà.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-223">As discussed previously, there is already the required functionality to save the state in an `IStorageManager` implementation.</span></span> <span data-ttu-id="d3fa1-224">Nous devons maintenant intégrer ce avec le runtime WCF.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-224">We now must integrate this with the WCF runtime.</span></span> <span data-ttu-id="d3fa1-225">Un autre attribut est requis et est applicable aux méthodes de la classe d'implémentation de service.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-225">Another attribute is required that is applicable to the methods in the service implementation class.</span></span> <span data-ttu-id="d3fa1-226">Cet attribut est supposé s'appliquer aux méthodes qui modifient l'état de l'instance de service.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-226">This attribute is supposed to be applied to the methods that change the state of the service instance.</span></span>

<span data-ttu-id="d3fa1-227">La classe `SaveStateAttribute` implémente ces fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-227">The `SaveStateAttribute` class implements this functionality.</span></span> <span data-ttu-id="d3fa1-228">Il implémente également `IOperationBehavior` la classe pour modifier le runtime WCF pour chaque opération.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-228">It also implements `IOperationBehavior` class to modify the WCF runtime for each operation.</span></span> <span data-ttu-id="d3fa1-229">Quand une méthode est marquée avec cet attribut, le runtime WCF appelle la `ApplyBehavior` méthode pendant la construction de `DispatchOperation` la appropriée.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-229">When a method is marked with this attribute, the WCF runtime invokes the `ApplyBehavior` method while the appropriate `DispatchOperation` is being constructed.</span></span> <span data-ttu-id="d3fa1-230">Cette implémentation de méthode comporte une seule ligne de code :</span><span class="sxs-lookup"><span data-stu-id="d3fa1-230">In this method implementation there is single line of code:</span></span>

```csharp
dispatch.Invoker = new OperationInvoker(dispatch.Invoker);
```

<span data-ttu-id="d3fa1-231">Cette instruction crée une instance de type `OperationInvoker` et l'assigne à la propriété `Invoker` du `DispatchOperation` en cours de construction.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-231">This instruction creates an instance of `OperationInvoker` type and assigns it to the `Invoker` property of the `DispatchOperation` being constructed.</span></span> <span data-ttu-id="d3fa1-232">La classe `OperationInvoker` est un wrapper pour le demandeur d'opération par défaut créé pour `DispatchOperation`.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-232">The `OperationInvoker` class is a wrapper for the default operation invoker created for the `DispatchOperation`.</span></span> <span data-ttu-id="d3fa1-233">Cette classe implémente l’interface `IOperationInvoker`.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-233">This class implements the `IOperationInvoker` interface.</span></span> <span data-ttu-id="d3fa1-234">Dans l'implémentation de méthode `Invoke`, l'appel de méthode réel est délégué au demandeur d'opération interne.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-234">In the `Invoke` method implementation the actual method invocation is delegated to the inner operation invoker.</span></span> <span data-ttu-id="d3fa1-235">Toutefois, avant de retourner les résultats, le gestionnaire de stockage du `InstanceContext` est utilisé pour enregistrer l'instance de service.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-235">However, before returning the results the storage manager in the `InstanceContext` is used to save the service instance.</span></span>

```csharp
object result = innerOperationInvoker.Invoke(instance,
    inputs, out outputs);

// Save the instance using the storage manager saved in the
// current InstanceContext.
InstanceContextExtension extension =
    OperationContext.Current.InstanceContext.Extensions.Find<InstanceContextExtension>();

extension.StorageManager.SaveInstance(extension.ContextId, instance);
return result;
```

## <a name="using-the-extension"></a><span data-ttu-id="d3fa1-236">Utilisation de l'extension</span><span class="sxs-lookup"><span data-stu-id="d3fa1-236">Using the Extension</span></span>

<span data-ttu-id="d3fa1-237">La couche de canal et les extensions de couche de modèle de service sont toutes deux effectuées et peuvent désormais être utilisées dans les applications WCF.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-237">Both the channel layer and service model layer extensions are done and they can now be used in WCF applications.</span></span> <span data-ttu-id="d3fa1-238">Les services doivent ajouter le canal dans la pile de canaux à l’aide d’une liaison personnalisée, puis marquer les classes d’implémentation de service avec les attributs appropriés.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-238">Services have to add the channel into the channel stack using a custom binding and then mark the service implementation classes with the appropriate attributes.</span></span>

```csharp
[DurableInstanceContext]
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]
public class ShoppingCart : IShoppingCart
{
//…
     [SaveState]
     public int AddItem(string item)
     {
         //…
     }
//…
 }
```

<span data-ttu-id="d3fa1-239">Les applications clientes doivent ajouter DurableInstanceContextChannel dans la pile de canaux à l’aide d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-239">Client applications must add the DurableInstanceContextChannel into the channel stack using a custom binding.</span></span> <span data-ttu-id="d3fa1-240">Pour configurer le canal de façon déclarative dans le fichier de configuration, la section d'élément de liaison doit être ajoutée à la collection d'extensions d'élément de liaison.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-240">To configure the channel declaratively in the configuration file, the binding element section has to be added to the binding element extensions collection.</span></span>

```xml
<system.serviceModel>
 <extensions>
   <bindingElementExtensions>
     <add name="durableInstanceContext"
type="Microsoft.ServiceModel.Samples.DurableInstanceContextBindingElementSection, DurableInstanceContextExtension, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null"/>
   </bindingElementExtensions>
 </extensions>
</system.serviceModel>
```

<span data-ttu-id="d3fa1-241">L’élément de liaison peut maintenant être utilisé avec une liaison personnalisée à l’instar des autres éléments de liaison standard :</span><span class="sxs-lookup"><span data-stu-id="d3fa1-241">Now the binding element can be used with a custom binding just like other standard binding elements:</span></span>

```xml
<bindings>
 <customBinding>
   <binding name="TextOverHttp">
     <durableInstanceContext contextType="HttpCookie"/>
     <reliableSession />
     <textMessageEncoding />
     <httpTransport />
   </binding>
 </customBinding>
</bindings>
```

## <a name="conclusion"></a><span data-ttu-id="d3fa1-242">Conclusion</span><span class="sxs-lookup"><span data-stu-id="d3fa1-242">Conclusion</span></span>

<span data-ttu-id="d3fa1-243">Cet exemple a montré comment créer un canal de protocole personnalisé et comment personnaliser le comportement de service permettant de l'activer.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-243">This sample showed how to create a custom protocol channel and how to customize the service behavior to enable it.</span></span>

<span data-ttu-id="d3fa1-244">L’extension peut encore être améliorée en permettant aux utilisateurs de spécifier l’implémentation `IStorageManager` à l’aide d’une section de configuration.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-244">The extension can be further improved by letting users specify the `IStorageManager` implementation using a configuration section.</span></span> <span data-ttu-id="d3fa1-245">Cela permet de modifier le magasin de sauvegarde sans avoir à recompiler le code de service.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-245">This makes it possible to modify the backing store without recompiling the service code.</span></span>

<span data-ttu-id="d3fa1-246">En outre, vous pouvez essayer d'implémenter une classe (par exemple, `StateBag`) qui encapsule l'état de l'instance.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-246">Furthermore you could try to implement a class (for example, `StateBag`), which encapsulates the state of the instance.</span></span> <span data-ttu-id="d3fa1-247">Cette classe est chargée de rendre l'état persistant chaque fois qu'il change.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-247">That class is responsible for persisting the state whenever it changes.</span></span> <span data-ttu-id="d3fa1-248">De cette manière, vous pouvez éviter d'utiliser l'attribut `SaveState` et travailler de manière plus précise (par exemple, vous pouvez rendre l'état persistant lorsqu'il est réellement modifié plutôt que de l'enregistrer chaque fois qu'une méthode avec l'attribut `SaveState` est appelée).</span><span class="sxs-lookup"><span data-stu-id="d3fa1-248">This way you can avoid using the `SaveState` attribute and perform the persisting work more accurately (for example, you could persist the state when the state is actually changed rather than saving it each time when a method with the `SaveState` attribute is called).</span></span>

<span data-ttu-id="d3fa1-249">Lorsque vous exécutez l'exemple, la sortie suivante s'affiche.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-249">When you run the sample, the following output is displayed.</span></span> <span data-ttu-id="d3fa1-250">Le client ajoute deux éléments à son panier d'achat puis place la liste d'éléments dans celui-ci à partir du service.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-250">The client adds two items to its shopping cart and then gets the list of items in its shopping cart from the service.</span></span> <span data-ttu-id="d3fa1-251">Appuyez sur ENTER dans chaque fenêtre de console pour arrêter le service et le client.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-251">Press ENTER in each console window to shut down the service and client.</span></span>

```console
Enter the name of the product: apples
Enter the name of the product: bananas

Shopping cart currently contains the following items.
apples
bananas
Press ENTER to shut down client
```

> [!NOTE]
> <span data-ttu-id="d3fa1-252">La reconstruction du service remplace le fichier de base de données.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-252">Rebuilding the service overwrites the database file.</span></span> <span data-ttu-id="d3fa1-253">Pour observer l'état conservé sur plusieurs exécutions de l'exemple, ne reconstruisez pas l'exemple d'une exécution à l'autre.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-253">To observe state preserved across multiple runs of the sample, be sure not to rebuild the sample between runs.</span></span>

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d3fa1-254">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="d3fa1-254">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="d3fa1-255">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d3fa1-255">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="d3fa1-256">Pour générer la solution, suivez les instructions de [la création des exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d3fa1-256">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="d3fa1-257">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d3fa1-257">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

> [!NOTE]
> <span data-ttu-id="d3fa1-258">Vous devez exécuter SQL Server 2005 ou SQL Express 2005 pour exécuter cet exemple.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-258">You must be running SQL Server 2005 or SQL Express 2005 to run this sample.</span></span> <span data-ttu-id="d3fa1-259">Si vous exécutez SQL Server 2005, vous devez modifier la configuration de la chaîne de connexion du service.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-259">If you are running SQL Server 2005, you must modify the configuration of the service's connection string.</span></span> <span data-ttu-id="d3fa1-260">Lors de l'exécution sur plusieurs ordinateurs, SQL Server est uniquement requis sur l'ordinateur serveur.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-260">When running cross-machine, SQL Server is only required on the server machine.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d3fa1-261">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-261">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d3fa1-262">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-262">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="d3fa1-263">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ) et.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-263">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d3fa1-264">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="d3fa1-264">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Durable`
