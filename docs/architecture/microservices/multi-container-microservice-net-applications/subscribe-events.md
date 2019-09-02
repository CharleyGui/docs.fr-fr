---
title: S’abonner à des événements
description: Architecture de microservices .NET pour les applications .NET conteneurisées | Comprendre les détails de la publication et de l’abonnement à des événements d’intégration.
ms.date: 10/02/2018
ms.openlocfilehash: c0eaacce51b186191431bf827bb84d3a2d2b7b1f
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68675866"
---
# <a name="subscribing-to-events"></a><span data-ttu-id="95d21-103">S’abonner à des événements</span><span class="sxs-lookup"><span data-stu-id="95d21-103">Subscribing to events</span></span>

<span data-ttu-id="95d21-104">Pour utiliser Service Bus, vous devez d’abord abonner les microservices aux événements souhaités.</span><span class="sxs-lookup"><span data-stu-id="95d21-104">The first step for using the event bus is to subscribe the microservices to the events they want to receive.</span></span> <span data-ttu-id="95d21-105">Cette étape doit être effectuée dans les microservices récepteurs.</span><span class="sxs-lookup"><span data-stu-id="95d21-105">That should be done in the receiver microservices.</span></span>

<span data-ttu-id="95d21-106">L’exemple de code suivant montre ce que chaque microservice récepteur doit implémenter au démarrage du service (dans la classe `Startup`) pour s’abonner aux événements dont il a besoin.</span><span class="sxs-lookup"><span data-stu-id="95d21-106">The following simple code shows what each receiver microservice needs to implement when starting the service (that is, in the `Startup` class) so it subscribes to the events it needs.</span></span> <span data-ttu-id="95d21-107">Dans ce cas, le microservice `basket.api` doit s’abonner à `ProductPriceChangedIntegrationEvent` et aux messages `OrderStartedIntegrationEvent`.</span><span class="sxs-lookup"><span data-stu-id="95d21-107">In this case, the `basket.api` microservice needs to subscribe to `ProductPriceChangedIntegrationEvent` and the `OrderStartedIntegrationEvent` messages.</span></span>

<span data-ttu-id="95d21-108">Par exemple, lorsqu’il s’abonne à l’événement `ProductPriceChangedIntegrationEvent`, le microservice de panier d’achat est informé du changement de prix d’un produit et avertit l’utilisateur de ce changement si ce produit se trouve dans son panier.</span><span class="sxs-lookup"><span data-stu-id="95d21-108">For instance, when subscribing to the `ProductPriceChangedIntegrationEvent` event, that makes the basket microservice aware of any changes to the product price and lets it warn the user about the change if that product is in the user’s basket.</span></span>

```csharp
var eventBus = app.ApplicationServices.GetRequiredService<IEventBus>();

eventBus.Subscribe<ProductPriceChangedIntegrationEvent,
                   ProductPriceChangedIntegrationEventHandler>();

eventBus.Subscribe<OrderStartedIntegrationEvent,
                   OrderStartedIntegrationEventHandler>();

```

<span data-ttu-id="95d21-109">Lorsque ce code est exécuté, le microservice abonné écoute via les canaux RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="95d21-109">After this code runs, the subscriber microservice will be listening through RabbitMQ channels.</span></span> <span data-ttu-id="95d21-110">Quand un message de type ProductPriceChangedIntegrationEvent est reçu, le code appelle le gestionnaire d’événements qui lui est passé et traite l’événement.</span><span class="sxs-lookup"><span data-stu-id="95d21-110">When any message of type ProductPriceChangedIntegrationEvent arrives, the code invokes the event handler that is passed to it and processes the event.</span></span>

## <a name="publishing-events-through-the-event-bus"></a><span data-ttu-id="95d21-111">Publication d’événements via le bus d’événements</span><span class="sxs-lookup"><span data-stu-id="95d21-111">Publishing events through the event bus</span></span>

<span data-ttu-id="95d21-112">Enfin, l’expéditeur du message (le microservice d’origine) publie les événements d’intégration avec du code similaire à celui de l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="95d21-112">Finally, the message sender (origin microservice) publishes the integration events with code similar to the following example.</span></span> <span data-ttu-id="95d21-113">Il s’agit d’un exemple simplifié qui ne prend pas en compte l’atomicité. Vous devez implémenter un code similaire à celui-ci chaque fois qu’un événement doit être propagé sur plusieurs microservices, en général, juste après la validation de données ou de transactions du microservice d’origine.</span><span class="sxs-lookup"><span data-stu-id="95d21-113">(This is a simplified example that does not take atomicity into account.) You would implement similar code whenever an event must be propagated across multiple microservices, usually right after committing data or transactions from the origin microservice.</span></span>

<span data-ttu-id="95d21-114">Tout d’abord, l’objet d’implémentation du bus d’événements (basé sur RabbitMQ ou sur un bus de services) est injecté dans le constructeur du contrôleur, comme dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="95d21-114">First, the event bus implementation object (based on RabbitMQ or based on a service bus) would be injected at the controller constructor, as in the following code:</span></span>

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    private readonly CatalogContext _context;
    private readonly IOptionsSnapshot<Settings> _settings;
    private readonly IEventBus _eventBus;

    public CatalogController(CatalogContext context,
        IOptionsSnapshot<Settings> settings,
        IEventBus eventBus)
    {
        _context = context;
        _settings = settings;
        _eventBus = eventBus;
    }
    // ...
}
```

<span data-ttu-id="95d21-115">Ensuite, utilisez-le à partir des méthodes de votre contrôleur, comme dans la méthode UpdateProduct :</span><span class="sxs-lookup"><span data-stu-id="95d21-115">Then you use it from your controller’s methods, like in the UpdateProduct method:</span></span>

```csharp
[Route("items")]
[HttpPost]
public async Task<IActionResult> UpdateProduct([FromBody]CatalogItem product)
{
    var item = await _context.CatalogItems.SingleOrDefaultAsync(
        i => i.Id == product.Id);
    // ...
    if (item.Price != product.Price)
    {
        var oldPrice = item.Price;
        item.Price = product.Price;
        _context.CatalogItems.Update(item);
        var @event = new ProductPriceChangedIntegrationEvent(item.Id,
            item.Price,
            oldPrice);
        // Commit changes in original transaction
        await _context.SaveChangesAsync();
        // Publish integration event to the event bus
        // (RabbitMQ or a service bus underneath)
        _eventBus.Publish(@event);
        // ...
    }
    // ...
}
```

<span data-ttu-id="95d21-116">Dans ce cas, le microservice d’origine étant un microservice CRUD simple, le code est placé dans un contrôleur d’API web.</span><span class="sxs-lookup"><span data-stu-id="95d21-116">In this case, since the origin microservice is a simple CRUD microservice, that code is placed right into a Web API controller.</span></span>

<span data-ttu-id="95d21-117">Dans les microservices plus avancés, comme avec l’approche CQRS, vous pouvez l’implémenter dans la classe `CommandHandler`, dans la méthode `Handle()`.</span><span class="sxs-lookup"><span data-stu-id="95d21-117">In more advanced microservices, like when using CQRS approaches, it can be implemented in the `CommandHandler` class, within the `Handle()` method.</span></span>

### <a name="designing-atomicity-and-resiliency-when-publishing-to-the-event-bus"></a><span data-ttu-id="95d21-118">Conception de l’atomicité et de la résilience lors de la publication d’événements dans le bus d’événements</span><span class="sxs-lookup"><span data-stu-id="95d21-118">Designing atomicity and resiliency when publishing to the event bus</span></span>

<span data-ttu-id="95d21-119">Quand vous publiez des événements d’intégration par le biais d’un système de messagerie distribuée comme votre bus d’événements, vous être confronté au problème de mettre à jour la base de données d’origine et de publier un événement de manière atomique (autrement dit, les deux opérations se terminent ou aucune des deux ne se termine).</span><span class="sxs-lookup"><span data-stu-id="95d21-119">When you publish integration events through a distributed messaging system like your event bus, you have the problem of atomically updating the original database and publishing an event (that is, either both operations complete or none of them).</span></span> <span data-ttu-id="95d21-120">Par exemple, dans l’exemple simplifié précédent, le code valide les données dans la base de données lorsque le prix du produit est modifié, puis il publie un message ProductPriceChangedIntegrationEvent.</span><span class="sxs-lookup"><span data-stu-id="95d21-120">For instance, in the simplified example shown earlier, the code commits data to the database when the product price is changed and then publishes a ProductPriceChangedIntegrationEvent message.</span></span> <span data-ttu-id="95d21-121">Au début, il peut paraître essentiel que ces deux opérations soient effectuées de manière atomique.</span><span class="sxs-lookup"><span data-stu-id="95d21-121">Initially, it might look essential that these two operations be performed atomically.</span></span> <span data-ttu-id="95d21-122">Toutefois, si vous utilisez une transaction distribuée impliquant la base de données et le répartiteur de messages, comme vous le feriez sur les anciens systèmes tels que [Microsoft Message Queuing (MSMQ)](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx), cette méthode n’est pas recommandée pour les raisons énoncées par le [théorème CAP](https://www.quora.com/What-Is-CAP-Theorem-1).</span><span class="sxs-lookup"><span data-stu-id="95d21-122">However, if you are using a distributed transaction involving the database and the message broker, as you do in older systems like [Microsoft Message Queuing (MSMQ)](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx), this is not recommended for the reasons described by the [CAP theorem](https://www.quora.com/What-Is-CAP-Theorem-1).</span></span>

<span data-ttu-id="95d21-123">Pour résumer, vous utilisez des microservices pour créer des systèmes évolutifs et hautement disponibles.</span><span class="sxs-lookup"><span data-stu-id="95d21-123">Basically, you use microservices to build scalable and highly available systems.</span></span> <span data-ttu-id="95d21-124">Pour simplifier quelque peu, le théorème CAP dit qu’il n’est pas possible de générer une base de données (distribuée) (ou un microservice propriétaire de son modèle) qui soit continuellement disponible, fortement cohérente *et* tolérante à toutes les partitions.</span><span class="sxs-lookup"><span data-stu-id="95d21-124">Simplifying somewhat, the CAP theorem says that you cannot build a (distributed) database (or a microservice that owns its model) that is continually available, strongly consistent, *and* tolerant to any partition.</span></span> <span data-ttu-id="95d21-125">Vous ne pouvez avoir que deux de ces propriétés à la fois.</span><span class="sxs-lookup"><span data-stu-id="95d21-125">You must choose two of these three properties.</span></span>

<span data-ttu-id="95d21-126">Dans les architectures basées sur les microservices, vous devez choisir la disponibilité et la tolérance, et donner moins d’importance à la cohérence.</span><span class="sxs-lookup"><span data-stu-id="95d21-126">In microservices-based architectures, you should choose availability and tolerance, and you should deemphasize strong consistency.</span></span> <span data-ttu-id="95d21-127">Par conséquent, dans les applications de microservice les plus récentes, il n’est généralement pas souhaitable d’utiliser des transactions distribuées pour la messagerie, comme vous le feriez pour implémenter des [transactions distribuées](https://docs.microsoft.com/previous-versions/windows/desktop/ms681205(v=vs.85)) DTC avec [MSMQ](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="95d21-127">Therefore, in most modern microservice-based applications, you usually do not want to use distributed transactions in messaging, as you do when you implement [distributed transactions](https://docs.microsoft.com/previous-versions/windows/desktop/ms681205(v=vs.85)) based on the Windows Distributed Transaction Coordinator (DTC) with [MSMQ](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx).</span></span>

<span data-ttu-id="95d21-128">Revenons au problème de départ et à son exemple.</span><span class="sxs-lookup"><span data-stu-id="95d21-128">Let’s go back to the initial issue and its example.</span></span> <span data-ttu-id="95d21-129">Si le service tombe en panne après la mise à jour de la base de données (dans ce cas, juste après la ligne de code avec \_context.SaveChangesAsync()), mais avant la publication de l’événement d’intégration, l’ensemble du système risque de devenir incohérent.</span><span class="sxs-lookup"><span data-stu-id="95d21-129">If the service crashes after the database is updated (in this case, right after the line of code with \_context.SaveChangesAsync()), but before the integration event is published, the overall system could become inconsistent.</span></span> <span data-ttu-id="95d21-130">Cela peut être critique pour l’entreprise, selon le type d’opération.</span><span class="sxs-lookup"><span data-stu-id="95d21-130">This might be business critical, depending on the specific business operation you are dealing with.</span></span>

<span data-ttu-id="95d21-131">Comme déjà mentionné dans la section relative à l’architecture, plusieurs méthodes permettent de traiter ce problème :</span><span class="sxs-lookup"><span data-stu-id="95d21-131">As mentioned earlier in the architecture section, you can have several approaches for dealing with this issue:</span></span>

- <span data-ttu-id="95d21-132">Utiliser la version complète du [modèle d’approvisionnement en événements](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)</span><span class="sxs-lookup"><span data-stu-id="95d21-132">Using the full [Event Sourcing pattern](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing).</span></span>

- <span data-ttu-id="95d21-133">Utiliser [l’exploration des données du journal des transactions](https://www.scoop.it/t/sql-server-transaction-log-mining)</span><span class="sxs-lookup"><span data-stu-id="95d21-133">Using [transaction log mining](https://www.scoop.it/t/sql-server-transaction-log-mining).</span></span>

- <span data-ttu-id="95d21-134">Utiliser le [modèle de boîte d’envoi](http://gistlabs.com/2014/05/the-outbox/)</span><span class="sxs-lookup"><span data-stu-id="95d21-134">Using the [Outbox pattern](http://gistlabs.com/2014/05/the-outbox/).</span></span> <span data-ttu-id="95d21-135">Il s’agit d’une table transactionnelle permettant de stocker les événements d’intégration (en étendant la transaction locale).</span><span class="sxs-lookup"><span data-stu-id="95d21-135">This is a transactional table to store the integration events (extending the local transaction).</span></span>

<span data-ttu-id="95d21-136">Pour ce scénario, l’utilisation du modèle d’approvisionnement en événements est l’une des meilleures approches, sinon *la* meilleure.</span><span class="sxs-lookup"><span data-stu-id="95d21-136">For this scenario, using the full Event Sourcing (ES) pattern is one of the best approaches, if not *the* best.</span></span> <span data-ttu-id="95d21-137">Toutefois, dans de nombreux scénarios d’application, vous ne pourrez pas implémenter un système d’approvisionnement en événements complet.</span><span class="sxs-lookup"><span data-stu-id="95d21-137">However, in many application scenarios, you might not be able to implement a full ES system.</span></span> <span data-ttu-id="95d21-138">Avec l’approvisionnement en événements, vous stockez uniquement des événements de domaine dans votre base de données transactionnelle, au lieu de stocker les données de l’état actuel.</span><span class="sxs-lookup"><span data-stu-id="95d21-138">ES means storing only domain events in your transactional database, instead of storing current state data.</span></span> <span data-ttu-id="95d21-139">Le fait de stocker uniquement les événements de domaine comporte des avantages, tels que la disponibilité de l’historique de votre système et la capacité à déterminer l’état antérieur de votre système.</span><span class="sxs-lookup"><span data-stu-id="95d21-139">Storing only domain events can have great benefits, such as having the history of your system available and being able to determine the state of your system at any moment in the past.</span></span> <span data-ttu-id="95d21-140">Toutefois, l’implémentation d’un système d’approvisionnement en événements complet nécessite la modification d’une grande partie de l’architecture de votre système, et ajoute de nombreuses exigences et davantage de complexité.</span><span class="sxs-lookup"><span data-stu-id="95d21-140">However, implementing a full ES system requires you to rearchitect most of your system and introduces many other complexities and requirements.</span></span> <span data-ttu-id="95d21-141">Par exemple, vous pouvez utiliser une base de données créée spécialement pour l’approvisionnement en événements, telle qu’un [magasin d’événements](https://eventstore.org/), ou une base de données orientée documents, telle qu’Azure Cosmos DB, MongoDB, Cassandra, CouchDB ou RavenDB.</span><span class="sxs-lookup"><span data-stu-id="95d21-141">For example, you would want to use a database specifically made for event sourcing, such as [Event Store](https://eventstore.org/), or a document-oriented database such as Azure Cosmos DB, MongoDB, Cassandra, CouchDB, or RavenDB.</span></span> <span data-ttu-id="95d21-142">L’approvisionnement en événements est une excellente approche pour ce problème, mais ce n’est pas la plus simple, sauf si vous êtes déjà familiarisé avec l’approvisionnement en événements.</span><span class="sxs-lookup"><span data-stu-id="95d21-142">ES is a great approach for this problem, but not the easiest solution unless you are already familiar with event sourcing.</span></span>

<span data-ttu-id="95d21-143">L’exploration du journal des transactions peut paraître simple au premier abord.</span><span class="sxs-lookup"><span data-stu-id="95d21-143">The option to use transaction log mining initially looks very transparent.</span></span> <span data-ttu-id="95d21-144">Toutefois, pour cette méthode, vous devez associer le microservice à votre journal des transactions SGBDR, comme par exemple le journal des transactions SQL Server.</span><span class="sxs-lookup"><span data-stu-id="95d21-144">However, to use this approach, the microservice has to be coupled to your RDBMS transaction log, such as the SQL Server transaction log.</span></span> <span data-ttu-id="95d21-145">Toutefois, cela n’est pas souhaitable.</span><span class="sxs-lookup"><span data-stu-id="95d21-145">This is probably not desirable.</span></span> <span data-ttu-id="95d21-146">Un autre inconvénient à cela est que les mises à jour de bas niveau enregistrées dans le journal des transactions peuvent ne pas être au même niveau que les événements d’intégration de haut niveau.</span><span class="sxs-lookup"><span data-stu-id="95d21-146">Another drawback is that the low-level updates recorded in the transaction log might not be at the same level as your high-level integration events.</span></span> <span data-ttu-id="95d21-147">Si c’est le cas, il peut être difficile d’effectuer une rétroconception sur les opérations du journal des transactions.</span><span class="sxs-lookup"><span data-stu-id="95d21-147">If so, the process of reverse-engineering those transaction log operations can be difficult.</span></span>

<span data-ttu-id="95d21-148">La meilleure approche consiste à combiner une table de base de données transactionnelle et un modèle simplifié d’approvisionnement en événements.</span><span class="sxs-lookup"><span data-stu-id="95d21-148">A balanced approach is a mix of a transactional database table and a simplified ES pattern.</span></span> <span data-ttu-id="95d21-149">Vous pouvez utiliser un état du type « prêt à publier l’événement », que vous définissez dans l’événement d’origine lorsque vous le validez dans la table d’événements d’intégration.</span><span class="sxs-lookup"><span data-stu-id="95d21-149">You can use a state such as “ready to publish the event,” which you set in the original event when you commit it to the integration events table.</span></span> <span data-ttu-id="95d21-150">Ensuite, vous essayez de publier l’événement dans le bus d’événements.</span><span class="sxs-lookup"><span data-stu-id="95d21-150">You then try to publish the event to the event bus.</span></span> <span data-ttu-id="95d21-151">Si l’action de publication de l’événement réussit, démarrez une autre transaction dans le service d’origine, puis remplacez l’état « prêt à publier l’événement » par l’état « événement déjà publié ».</span><span class="sxs-lookup"><span data-stu-id="95d21-151">If the publish-event action succeeds, you start another transaction in the origin service and move the state from “ready to publish the event” to “event already published.”</span></span>

<span data-ttu-id="95d21-152">Si l’action de publication de l’événement échoue dans le bus d’événements, les données ne seront toujours pas incohérentes dans le microservice d’origine. Elles continueront d’être signalées comme étant « prêtes à publier l’événement », et par rapport aux autres services, elles seront cohérentes à terme.</span><span class="sxs-lookup"><span data-stu-id="95d21-152">If the publish-event action in the event bus fails, the data still will not be inconsistent within the origin microservice—it is still marked as “ready to publish the event,” and with respect to the rest of the services, it will eventually be consistent.</span></span> <span data-ttu-id="95d21-153">Vous pouvez toujours avoir des tâches en arrière-plan qui vérifient l’état des transactions ou des événements d’intégration.</span><span class="sxs-lookup"><span data-stu-id="95d21-153">You can always have background jobs checking the state of the transactions or integration events.</span></span> <span data-ttu-id="95d21-154">Si la tâche détecte un événement avec l’état « prêt à publier l’événement », elle peut tenter de republier cet événement dans le bus d’événements.</span><span class="sxs-lookup"><span data-stu-id="95d21-154">If the job finds an event in the “ready to publish the event” state, it can try to republish that event to the event bus.</span></span>

<span data-ttu-id="95d21-155">Notez qu’avec cette approche, vous conservez uniquement les événements d’intégration de chaque microservice d’origine, et uniquement les événements que vous souhaitez communiquer aux autres microservices ou systèmes externes.</span><span class="sxs-lookup"><span data-stu-id="95d21-155">Notice that with this approach, you are persisting only the integration events for each origin microservice, and only the events that you want to communicate to other microservices or external systems.</span></span> <span data-ttu-id="95d21-156">En revanche, dans un système d’approvisionnement en événements complet, tous les événements de domaine sont également stockés.</span><span class="sxs-lookup"><span data-stu-id="95d21-156">In contrast, in a full ES system, you store all domain events as well.</span></span>

<span data-ttu-id="95d21-157">Par conséquent, cette approche mixte n’est autre qu’un système simplifié d’approvisionnement en événements.</span><span class="sxs-lookup"><span data-stu-id="95d21-157">Therefore, this balanced approach is a simplified ES system.</span></span> <span data-ttu-id="95d21-158">Vous avez besoin de la liste des événements d’intégration avec leur état actuel (« prêt pour la publication » ou« publié »).</span><span class="sxs-lookup"><span data-stu-id="95d21-158">You need a list of integration events with their current state (“ready to publish” versus “published”).</span></span> <span data-ttu-id="95d21-159">Toutefois, vous avez uniquement besoin d’implémenter ces états pour les événements d’intégration.</span><span class="sxs-lookup"><span data-stu-id="95d21-159">But you only need to implement these states for the integration events.</span></span> <span data-ttu-id="95d21-160">En outre, avec cette approche, il n’est pas nécessaire de stocker toutes les données de votre domaine comme des événements dans la base de données transactionnelle, comme vous le feriez dans un système d’approvisionnement en événements complet.</span><span class="sxs-lookup"><span data-stu-id="95d21-160">And in this approach, you do not need to store all your domain data as events in the transactional database, as you would in a full ES system.</span></span>

<span data-ttu-id="95d21-161">Si vous utilisez déjà une base de données relationnelle, vous pouvez utiliser une table transactionnelle pour stocker les événements d’intégration.</span><span class="sxs-lookup"><span data-stu-id="95d21-161">If you are already using a relational database, you can use a transactional table to store integration events.</span></span> <span data-ttu-id="95d21-162">Pour obtenir l’atomicité de votre application, vous devez utiliser un processus en deux étapes basé sur les transactions locales.</span><span class="sxs-lookup"><span data-stu-id="95d21-162">To achieve atomicity in your application, you use a two-step process based on local transactions.</span></span> <span data-ttu-id="95d21-163">Pour résumer, une table IntegrationEvent doit se trouver dans la même base de données que vos entités de domaine.</span><span class="sxs-lookup"><span data-stu-id="95d21-163">Basically, you have an IntegrationEvent table in the same database where you have your domain entities.</span></span> <span data-ttu-id="95d21-164">Cette table fonctionne comme une garantie d’obtention de l’atomicité, et vous permet d’inclure les événements d’intégration persistants dans les transactions qui valident vos données de domaine.</span><span class="sxs-lookup"><span data-stu-id="95d21-164">That table works as an insurance for achieving atomicity so that you include persisted integration events into the same transactions that are committing your domain data.</span></span>

<span data-ttu-id="95d21-165">Voici, étape par étape, le déroulement de ce processus :</span><span class="sxs-lookup"><span data-stu-id="95d21-165">Step by step, the process goes like this:</span></span>

1. <span data-ttu-id="95d21-166">L’application commence une transaction de base de données locale.</span><span class="sxs-lookup"><span data-stu-id="95d21-166">The application begins a local database transaction.</span></span>

2. <span data-ttu-id="95d21-167">Ensuite, elle met à jour l’état de vos entités de domaine et insère un événement dans la table d’événements d’intégration.</span><span class="sxs-lookup"><span data-stu-id="95d21-167">It then updates the state of your domain entities and inserts an event into the integration event table.</span></span>

3. <span data-ttu-id="95d21-168">Enfin, elle valide la transaction pour vous permettre d’obtenir l’atomicité souhaitée, puis</span><span class="sxs-lookup"><span data-stu-id="95d21-168">Finally, it commits the transaction, so you get the desired atomicity and then</span></span>

4. <span data-ttu-id="95d21-169">Vous publiez l’événement d’une manière ou d’une autre (à venir).</span><span class="sxs-lookup"><span data-stu-id="95d21-169">You publish the event somehow (next).</span></span>

<span data-ttu-id="95d21-170">Lorsque vous implémentez les étapes de publication des événements, vous avez les possibilités suivantes :</span><span class="sxs-lookup"><span data-stu-id="95d21-170">When implementing the steps of publishing the events, you have these choices:</span></span>

- <span data-ttu-id="95d21-171">Publiez l’événement d’intégration juste après la validation de la transaction, puis utilisez une autre transaction locale pour marquer les événements de la table comme étant publiés.</span><span class="sxs-lookup"><span data-stu-id="95d21-171">Publish the integration event right after committing the transaction and use another local transaction to mark the events in the table as being published.</span></span> <span data-ttu-id="95d21-172">Ensuite, utilisez la table comme un artefact pour effectuer le suivi des événements d’intégration en cas de problèmes au niveau des microservices distants, puis effectuez des actions compensatoires en fonction des événements d’intégration stockés.</span><span class="sxs-lookup"><span data-stu-id="95d21-172">Then, use the table just as an artifact to track the integration events in case of issues in the remote microservices, and perform compensatory actions based on the stored integration events.</span></span>

- <span data-ttu-id="95d21-173">Utilisez la table comme un type de file d’attente.</span><span class="sxs-lookup"><span data-stu-id="95d21-173">Use the table as a kind of queue.</span></span> <span data-ttu-id="95d21-174">Un thread d’application ou un processus distinct interroge la table d’événements d’intégration, publie les événements dans le bus d’événements, puis utilise une transaction locale pour marquer les événements comme étant publiés.</span><span class="sxs-lookup"><span data-stu-id="95d21-174">A separate application thread or process queries the integration event table, publishes the events to the event bus, and then uses a local transaction to mark the events as published.</span></span>

<span data-ttu-id="95d21-175">La figure 6-22 montre l’architecture de la première de ces approches.</span><span class="sxs-lookup"><span data-stu-id="95d21-175">Figure 6-22 shows the architecture for the first of these approaches.</span></span>

![Une approche pour gérer l’atomicité lors de la publication d’événements : utiliser une transaction pour valider l’événement auprès d’une table de journal des événements, puis une autre transaction pour effectuer la publication (utilisée dans eShopOnContainers)](./media/image23.png)

<span data-ttu-id="95d21-177">**Figure 6-22.**</span><span class="sxs-lookup"><span data-stu-id="95d21-177">**Figure 6-22**.</span></span> <span data-ttu-id="95d21-178">Atomicité lors de la publication d’événements dans le bus d’événements</span><span class="sxs-lookup"><span data-stu-id="95d21-178">Atomicity when publishing events to the event bus</span></span>

<span data-ttu-id="95d21-179">Il manque à l’approche illustrée à la figure 6-22 un microservice de worker supplémentaire chargé de vérifier et de confirmer la publication des événements d’intégration.</span><span class="sxs-lookup"><span data-stu-id="95d21-179">The approach illustrated in Figure 6-22 is missing an additional worker microservice that is in charge of checking and confirming the success of the published integration events.</span></span> <span data-ttu-id="95d21-180">En cas d’échec, le microservice de worker de vérification supplémentaire peut lire les événements de la table et les republier (autrement dit, répétez l’étape 2).</span><span class="sxs-lookup"><span data-stu-id="95d21-180">In case of failure, that additional checker worker microservice can read events from the table and republish them, that is, repeat step number 2.</span></span>

<span data-ttu-id="95d21-181">Pour la deuxième approche, vous devez utiliser la table EventLog comme une file d’attente et toujours utiliser un microservice de worker pour publier les messages.</span><span class="sxs-lookup"><span data-stu-id="95d21-181">About the second approach: you use the EventLog table as a queue and always use a worker microservice to publish the messages.</span></span> <span data-ttu-id="95d21-182">Dans ce cas, le processus est similaire à celui illustré dans la figure 6-23.</span><span class="sxs-lookup"><span data-stu-id="95d21-182">In that case, the process is like that shown in Figure 6-23.</span></span> <span data-ttu-id="95d21-183">On y voit un microservice supplémentaire, ainsi que la table qui est la seule source lors de la publication d’événements.</span><span class="sxs-lookup"><span data-stu-id="95d21-183">This shows an additional microservice, and the table is the single source when publishing events.</span></span>

![Une autre approche pour gérer l’atomicité : publier dans une table de journal des événements, puis faire publier l’événement par un autre microservice (un Worker en arrière-plan).](./media/image24.png)

<span data-ttu-id="95d21-185">**Figure 6-23.**</span><span class="sxs-lookup"><span data-stu-id="95d21-185">**Figure 6-23**.</span></span> <span data-ttu-id="95d21-186">Atomicité lors de la publication d’événements dans le bus d’événements avec un microservice de worker</span><span class="sxs-lookup"><span data-stu-id="95d21-186">Atomicity when publishing events to the event bus with a worker microservice</span></span>

<span data-ttu-id="95d21-187">Par souci de simplicité, l’exemple eShopOnContainers utilise la première approche (sans processus ou microservices de vérification supplémentaires), ainsi que le bus d’événements.</span><span class="sxs-lookup"><span data-stu-id="95d21-187">For simplicity, the eShopOnContainers sample uses the first approach (with no additional processes or checker microservices) plus the event bus.</span></span> <span data-ttu-id="95d21-188">Toutefois, l’exemple eShopOnContainers ne gère pas tous les cas de défaillance.</span><span class="sxs-lookup"><span data-stu-id="95d21-188">However, the eShopOnContainers is not handling all possible failure cases.</span></span> <span data-ttu-id="95d21-189">Dans une application réelle déployée dans le cloud, vous devez accepter le fait que des problèmes surviendront un jour ou l’autre. Il est donc nécessaire d’implémenter cette logique de vérification et de renvoi.</span><span class="sxs-lookup"><span data-stu-id="95d21-189">In a real application deployed to the cloud, you must embrace the fact that issues will arise eventually, and you must implement that check and resend logic.</span></span> <span data-ttu-id="95d21-190">L’utilisation de la table comme une file d’attente peut se révéler plus efficace que la première approche si cette table est la seule source d’événements quand vous les publiez (avec le worker) à l’aide du bus d’événements.</span><span class="sxs-lookup"><span data-stu-id="95d21-190">Using the table as a queue can be more effective than the first approach if you have that table as a single source of events when publishing them (with the worker) through the event bus.</span></span>

### <a name="implementing-atomicity-when-publishing-integration-events-through-the-event-bus"></a><span data-ttu-id="95d21-191">Implémentation de l’atomicité lors de la publication d’événements d’intégration via le bus d’événements</span><span class="sxs-lookup"><span data-stu-id="95d21-191">Implementing atomicity when publishing integration events through the event bus</span></span>

<span data-ttu-id="95d21-192">Le code suivant montre comment vous pouvez créer une transaction impliquant plusieurs objets DbContext : un contexte lié aux données d’origine mises à jour, et le deuxième contexte lié à la table IntegrationEventLog.</span><span class="sxs-lookup"><span data-stu-id="95d21-192">The following code shows how you can create a single transaction involving multiple DbContext objects—one context related to the original data being updated, and the second context related to the IntegrationEventLog table.</span></span>

<span data-ttu-id="95d21-193">Notez que la transaction de l’exemple de code ci-dessous ne sera pas résiliente si les connexions à la base de données rencontrent un problème lorsque le code est exécuté.</span><span class="sxs-lookup"><span data-stu-id="95d21-193">Note that the transaction in the example code below will not be resilient if connections to the database have any issue at the time when the code is running.</span></span> <span data-ttu-id="95d21-194">Cela peut se produire dans les systèmes cloud comme Azure SQL DB, qui sont susceptibles de déplacer des bases de données d’un serveur à un autre.</span><span class="sxs-lookup"><span data-stu-id="95d21-194">This can happen in cloud-based systems like Azure SQL DB, which might move databases across servers.</span></span> <span data-ttu-id="95d21-195">Pour implémenter des transactions résilientes dans plusieurs contextes, consultez la section [Implémentation de connexions SQL à Entity Framework Core résilientes](../implement-resilient-applications/implement-resilient-entity-framework-core-sql-connections.md) plus loin dans ce guide.</span><span class="sxs-lookup"><span data-stu-id="95d21-195">For implementing resilient transactions across multiple contexts, see the [Implementing resilient Entity Framework Core SQL connections](../implement-resilient-applications/implement-resilient-entity-framework-core-sql-connections.md) section later in this guide.</span></span>

<span data-ttu-id="95d21-196">Pour plus de clarté, l’exemple suivant montre l’ensemble du processus dans un même bloc de code.</span><span class="sxs-lookup"><span data-stu-id="95d21-196">For clarity, the following example shows the whole process in a single piece of code.</span></span> <span data-ttu-id="95d21-197">En réalité, l’implémentation d’eShopOnContainers est refactorisée, et la logique est fractionnée en plusieurs classes, pour faciliter sa gestion.</span><span class="sxs-lookup"><span data-stu-id="95d21-197">However, the eShopOnContainers implementation is actually refactored and split this logic into multiple classes so it is easier to maintain.</span></span>

```csharp
// Update Product from the Catalog microservice
//
public async Task<IActionResult> UpdateProduct([FromBody]CatalogItem productToUpdate)
{
  var catalogItem =
       await _catalogContext.CatalogItems.SingleOrDefaultAsync(i => i.Id ==
                                                               productToUpdate.Id);
  if (catalogItem == null) return NotFound();

  bool raiseProductPriceChangedEvent = false;
  IntegrationEvent priceChangedEvent = null;

  if (catalogItem.Price != productToUpdate.Price)
          raiseProductPriceChangedEvent = true;

  if (raiseProductPriceChangedEvent) // Create event if price has changed
  {
      var oldPrice = catalogItem.Price;
      priceChangedEvent = new ProductPriceChangedIntegrationEvent(catalogItem.Id,
                                                                  productToUpdate.Price,
                                                                  oldPrice);
  }
  // Update current product
  catalogItem = productToUpdate;

  // Just save the updated product if the Product's Price hasn't changed.
  if (!raiseProductPriceChangedEvent)
  {
      await _catalogContext.SaveChangesAsync();
  }
  else  // Publish to event bus only if product price changed
  {
        // Achieving atomicity between original DB and the IntegrationEventLog
        // with a local transaction
        using (var transaction = _catalogContext.Database.BeginTransaction())
        {
           _catalogContext.CatalogItems.Update(catalogItem);
           await _catalogContext.SaveChangesAsync();

           // Save to EventLog only if product price changed
           if(raiseProductPriceChangedEvent)
               await _integrationEventLogService.SaveEventAsync(priceChangedEvent);

           transaction.Commit();
        }

      // Publish the integration event through the event bus
      _eventBus.Publish(priceChangedEvent);

      integrationEventLogService.MarkEventAsPublishedAsync(
                                                priceChangedEvent);
  }

  return Ok();
}

```

<span data-ttu-id="95d21-198">Une fois que l’événement d’intégration ProductPriceChangedIntegrationEvent a été créé, la transaction qui stocke l’opération de domaine d’origine (mise à jour de l’élément de catalogue) inclut également la persistance de l’événement dans la table EventLog.</span><span class="sxs-lookup"><span data-stu-id="95d21-198">After the ProductPriceChangedIntegrationEvent integration event is created, the transaction that stores the original domain operation (update the catalog item) also includes the persistence of the event in the EventLog table.</span></span> <span data-ttu-id="95d21-199">De cette façon, vous n’obtenez qu’une seule transaction, et vous pourrez toujours vérifier si les messages d’événement ont été envoyés.</span><span class="sxs-lookup"><span data-stu-id="95d21-199">This makes it a single transaction, and you will always be able to check whether event messages were sent.</span></span>

<span data-ttu-id="95d21-200">La table du journal des événements est mise à jour atomiquement avec l’opération de base de données d’origine, à l’aide d’une transaction locale dans la même base de données.</span><span class="sxs-lookup"><span data-stu-id="95d21-200">The event log table is updated atomically with the original database operation, using a local transaction against the same database.</span></span> <span data-ttu-id="95d21-201">Si l’une des opérations échoue, une exception est levée et la transaction restaure toute opération terminée, de manière à maintenir la cohérence entre les opérations de domaine et les messages d’événement envoyés enregistrés dans la table.</span><span class="sxs-lookup"><span data-stu-id="95d21-201">If any of the operations fail, an exception is thrown and the transaction rolls back any completed operation, thus maintaining consistency between the domain operations and the event messages saved to the table.</span></span>

### <a name="receiving-messages-from-subscriptions-event-handlers-in-receiver-microservices"></a><span data-ttu-id="95d21-202">Réception de messages provenant d’abonnements : les gestionnaires d’événements dans les microservices récepteurs</span><span class="sxs-lookup"><span data-stu-id="95d21-202">Receiving messages from subscriptions: event handlers in receiver microservices</span></span>

<span data-ttu-id="95d21-203">En plus de la logique d’abonnement aux événements, vous devez implémenter le code interne pour les gestionnaires d’événements d’intégration (comme une méthode de rappel).</span><span class="sxs-lookup"><span data-stu-id="95d21-203">In addition to the event subscription logic, you need to implement the internal code for the integration event handlers (like a callback method).</span></span> <span data-ttu-id="95d21-204">C’est dans le gestionnaire d’événements que vous spécifiez où les messages d’événement d’un certain type doivent être reçus et traités.</span><span class="sxs-lookup"><span data-stu-id="95d21-204">The event handler is where you specify where the event messages of a certain type will be received and processed.</span></span>

<span data-ttu-id="95d21-205">Un gestionnaire d’événements reçoit d’abord une instance d’événement provenant du bus d’événements.</span><span class="sxs-lookup"><span data-stu-id="95d21-205">An event handler first receives an event instance from the event bus.</span></span> <span data-ttu-id="95d21-206">Il localise ensuite le composant à traiter qui est lié à cet événement d’intégration, en propageant et en conservant l’événement en tant que changement d’état dans le récepteur de microservice.</span><span class="sxs-lookup"><span data-stu-id="95d21-206">Then it locates the component to be processed related to that integration event, propagating and persisting the event as a change in state in the receiver microservice.</span></span> <span data-ttu-id="95d21-207">Par exemple, si un événement ProductPriceChanged provient du microservice de catalogue, il est géré dans le microservice de panier d’achat et change également d’état dans le microservice de panier récepteur, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="95d21-207">For example, if a ProductPriceChanged event originates in the catalog microservice, it is handled in the basket microservice and changes the state in this receiver basket microservice as well, as shown in the following code.</span></span>

```csharp
namespace Microsoft.eShopOnContainers.Services.Basket.API.IntegrationEvents.EventHandling
{
    public class ProductPriceChangedIntegrationEventHandler :
        IIntegrationEventHandler<ProductPriceChangedIntegrationEvent>
    {
        private readonly IBasketRepository _repository;

        public ProductPriceChangedIntegrationEventHandler(
            IBasketRepository repository)
        {
            _repository = repository;
        }

        public async Task Handle(ProductPriceChangedIntegrationEvent @event)
        {
            var userIds = await _repository.GetUsers();
            foreach (var id in userIds)
            {
                var basket = await _repository.GetBasket(id);
                await UpdatePriceInBasketItems(@event.ProductId, @event.NewPrice, basket);
            }
        }

        private async Task UpdatePriceInBasketItems(int productId, decimal newPrice,
            CustomerBasket basket)
        {
            var itemsToUpdate = basket?.Items?.Where(x => int.Parse(x.ProductId) ==
                productId).ToList();
            if (itemsToUpdate != null)
            {
                foreach (var item in itemsToUpdate)
                {
                    if(item.UnitPrice != newPrice)
                    {
                        var originalPrice = item.UnitPrice;
                        item.UnitPrice = newPrice;
                        item.OldUnitPrice = originalPrice;
                    }
                }
                await _repository.UpdateBasket(basket);
            }
        }
    }
}
```

<span data-ttu-id="95d21-208">Le gestionnaire d’événements doit vérifier si le produit se trouve dans une des instances du panier d’achat.</span><span class="sxs-lookup"><span data-stu-id="95d21-208">The event handler needs to verify whether the product exists in any of the basket instances.</span></span> <span data-ttu-id="95d21-209">Il met également à jour le prix de chaque article associé.</span><span class="sxs-lookup"><span data-stu-id="95d21-209">It also updates the item price for each related basket line item.</span></span> <span data-ttu-id="95d21-210">Enfin, il crée une alerte pour l’utilisateur concernant le changement de prix, comme indiqué dans la figure 6-24.</span><span class="sxs-lookup"><span data-stu-id="95d21-210">Finally, it creates an alert to be displayed to the user about the price change, as shown in Figure 6-24.</span></span>

![Affichage dans le navigateur de la notification de changement de processus dans le panier de l’utilisateur.](./media/image25.png)

<span data-ttu-id="95d21-212">**Figure 6-24.**</span><span class="sxs-lookup"><span data-stu-id="95d21-212">**Figure 6-24**.</span></span> <span data-ttu-id="95d21-213">Affichage du changement de prix d’un article du panier, communiqué par les événements d’intégration</span><span class="sxs-lookup"><span data-stu-id="95d21-213">Displaying an item price change in a basket, as communicated by integration events</span></span>

## <a name="idempotency-in-update-message-events"></a><span data-ttu-id="95d21-214">Idempotence des événements de mise à jour des messages</span><span class="sxs-lookup"><span data-stu-id="95d21-214">Idempotency in update message events</span></span>

<span data-ttu-id="95d21-215">Un aspect important des événements de mise à jour des messages est qu’une défaillance se produisant à n’importe quel moment de la communication doit entraîner une nouvelle tentative de publication du message.</span><span class="sxs-lookup"><span data-stu-id="95d21-215">An important aspect of update message events is that a failure at any point in the communication should cause the message to be retried.</span></span> <span data-ttu-id="95d21-216">Sinon, une tâche en arrière-plan pourrait tenter de publier un événement qui a déjà été publié, ce qui aurait pour effet de créer une condition de concurrence.</span><span class="sxs-lookup"><span data-stu-id="95d21-216">Otherwise a background task might try to publish an event that has already been published, creating a race condition.</span></span> <span data-ttu-id="95d21-217">Vous devez faire en sorte que les mises à jour soient idempotentes ou qu’elles fournissent suffisamment d’informations pour que vous puissiez détecter le doublon, le supprimer et renvoyer une seule réponse.</span><span class="sxs-lookup"><span data-stu-id="95d21-217">You need to make sure that the updates are either idempotent or that they provide enough information to ensure that you can detect a duplicate, discard it, and send back only one response.</span></span>

<span data-ttu-id="95d21-218">Comme indiqué précédemment, l’idempotence signifie qu’une opération peut être effectuée plusieurs fois sans que le résultat soit modifié.</span><span class="sxs-lookup"><span data-stu-id="95d21-218">As noted earlier, idempotency means that an operation can be performed multiple times without changing the result.</span></span> <span data-ttu-id="95d21-219">Dans un environnement de messagerie, comme lorsque vous communiquez des événements, un événement est idempotent s’il peut être remis plusieurs fois sans modifier le résultat pour le microservice récepteur.</span><span class="sxs-lookup"><span data-stu-id="95d21-219">In a messaging environment, as when communicating events, an event is idempotent if it can be delivered multiple times without changing the result for the receiver microservice.</span></span> <span data-ttu-id="95d21-220">Cela peut être nécessaire en raison de la nature de l’événement, ou en raison de la façon dont le système gère l’événement.</span><span class="sxs-lookup"><span data-stu-id="95d21-220">This may be necessary because of the nature of the event itself, or because of the way the system handles the event.</span></span> <span data-ttu-id="95d21-221">L’idempotence des messages est importante dans les applications qui utilisent la messagerie, et pas seulement dans les applications qui implémentent le modèle de bus d’événements.</span><span class="sxs-lookup"><span data-stu-id="95d21-221">Message idempotency is important in any application that uses messaging, not just in applications that implement the event bus pattern.</span></span>

<span data-ttu-id="95d21-222">Un exemple d’opération idempotente est une instruction SQL qui insère des données dans une table uniquement si ces données ne s’y trouvent pas déjà.</span><span class="sxs-lookup"><span data-stu-id="95d21-222">An example of an idempotent operation is a SQL statement that inserts data into a table only if that data is not already in the table.</span></span> <span data-ttu-id="95d21-223">Quel que soit le nombre de fois que vous exécutez cette instruction SQL INSERT, le résultat sera le même et la table contiendra les mêmes données.</span><span class="sxs-lookup"><span data-stu-id="95d21-223">It does not matter how many times you run that insert SQL statement; the result will be the same—the table will contain that data.</span></span> <span data-ttu-id="95d21-224">Une telle idempotence peut également être nécessaire lorsque vous traitez des messages, si ces messages sont susceptibles d’être envoyés et donc traités plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="95d21-224">Idempotency like this can also be necessary when dealing with messages if the messages could potentially be sent and therefore processed more than once.</span></span> <span data-ttu-id="95d21-225">Par exemple, si la logique de nouvelle tentative fait qu’un émetteur envoie exactement le même message plusieurs fois, vous devez vous assurer qu’il est idempotent.</span><span class="sxs-lookup"><span data-stu-id="95d21-225">For instance, if retry logic causes a sender to send exactly the same message more than once, you need to make sure that it is idempotent.</span></span>

<span data-ttu-id="95d21-226">Il est possible de concevoir des messages idempotents.</span><span class="sxs-lookup"><span data-stu-id="95d21-226">It is possible to design idempotent messages.</span></span> <span data-ttu-id="95d21-227">Par exemple, vous pouvez créer un événement indiquant « fixer le prix du produit à 25 $ » au lieu de « ajouter 5 $ au prix du produit ».</span><span class="sxs-lookup"><span data-stu-id="95d21-227">For example, you can create an event that says "set the product price to $25" instead of "add $5 to the product price."</span></span> <span data-ttu-id="95d21-228">Vous pouvez traiter le premier message autant de fois que vous voulez, le résultat sera le même.</span><span class="sxs-lookup"><span data-stu-id="95d21-228">You could safely process the first message any number of times and the result will be the same.</span></span> <span data-ttu-id="95d21-229">Cependant, ce n’est pas vrai pour le deuxième message.</span><span class="sxs-lookup"><span data-stu-id="95d21-229">That is not true for the second message.</span></span> <span data-ttu-id="95d21-230">Mais même dans le premier cas, il n’est pas forcément souhaitable de traiter le premier événement, car le système peut avoir envoyé un événement de changement de prix plus récent et vous écraseriez ainsi le nouveau prix.</span><span class="sxs-lookup"><span data-stu-id="95d21-230">But even in the first case, you might not want to process the first event, because the system could also have sent a newer price-change event and you would be overwriting the new price.</span></span>

<span data-ttu-id="95d21-231">Un autre exemple peut être un événement de commande terminée propagé vers plusieurs abonnés.</span><span class="sxs-lookup"><span data-stu-id="95d21-231">Another example might be an order-completed event being propagated to multiple subscribers.</span></span> <span data-ttu-id="95d21-232">Il est important que les informations de commande ne soient mises à jour qu’une seule fois dans les autres systèmes, même s’il existe des événements de message en double pour le même événement de commande terminée.</span><span class="sxs-lookup"><span data-stu-id="95d21-232">It is important that order information be updated in other systems just once, even if there are duplicated message events for the same order-completed event.</span></span>

<span data-ttu-id="95d21-233">Il peut être utile d’attribuer une identité à chaque événement, pour que vous puissiez créer une logique selon laquelle un événement ne doit être traité qu’une seule fois pour chaque récepteur.</span><span class="sxs-lookup"><span data-stu-id="95d21-233">It is convenient to have some kind of identity per event so that you can create logic that enforces that each event is processed only once per receiver.</span></span>

<span data-ttu-id="95d21-234">Le traitement des messages est fondamentalement idempotent.</span><span class="sxs-lookup"><span data-stu-id="95d21-234">Some message processing is inherently idempotent.</span></span> <span data-ttu-id="95d21-235">Par exemple, si un système génère des images miniatures, le nombre de traitements du message concernant la génération des miniatures importe peu. Le résultat est que les miniatures sont générées et qu’elles sont identiques à chaque fois.</span><span class="sxs-lookup"><span data-stu-id="95d21-235">For example, if a system generates image thumbnails, it might not matter how many times the message about the generated thumbnail is processed; the outcome is that the thumbnails are generated and they are the same every time.</span></span> <span data-ttu-id="95d21-236">En revanche, les opérations telles que l’appel d’une passerelle de paiement pour prélever un montant sur une carte de crédit peuvent ne pas être idempotentes du tout.</span><span class="sxs-lookup"><span data-stu-id="95d21-236">On the other hand, operations such as calling a payment gateway to charge a credit card may not be idempotent at all.</span></span> <span data-ttu-id="95d21-237">Dans ce cas, vous devez être sûr que le fait de traiter un message plusieurs fois aura l’effet que vous attendez.</span><span class="sxs-lookup"><span data-stu-id="95d21-237">In these cases, you need to ensure that processing a message multiple times has the effect that you expect.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="95d21-238">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="95d21-238">Additional resources</span></span>

- <span data-ttu-id="95d21-239">**Honoring message idempotency**</span><span class="sxs-lookup"><span data-stu-id="95d21-239">**Honoring message idempotency**</span></span> <br/>
    <https://docs.microsoft.com/previous-versions/msp-n-p/jj591565(v=pandp.10)#honoring-message-idempotency>

## <a name="deduplicating-integration-event-messages"></a><span data-ttu-id="95d21-240">Déduplication des messages d’événements d’intégration</span><span class="sxs-lookup"><span data-stu-id="95d21-240">Deduplicating integration event messages</span></span>

<span data-ttu-id="95d21-241">Vous pouvez faire en sorte que les événements de message ne soient envoyés et traités qu’une seule une fois par abonné à différents niveaux.</span><span class="sxs-lookup"><span data-stu-id="95d21-241">You can make sure that message events are sent and processed just once per subscriber at different levels.</span></span> <span data-ttu-id="95d21-242">L’une des méthodes possibles consiste à utiliser la fonctionnalité de déduplication proposée par l’infrastructure de messagerie que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="95d21-242">One way is to use a deduplication feature offered by the messaging infrastructure you are using.</span></span> <span data-ttu-id="95d21-243">Une autre consiste à implémenter une logique personnalisée dans votre microservice de destination.</span><span class="sxs-lookup"><span data-stu-id="95d21-243">Another is to implement custom logic in your destination microservice.</span></span> <span data-ttu-id="95d21-244">La meilleure solution est d’avoir des validations à la fois au niveau du transport et au niveau de l’application.</span><span class="sxs-lookup"><span data-stu-id="95d21-244">Having validations at both the transport level and the application level is your best bet.</span></span>

### <a name="deduplicating-message-events-at-the-eventhandler-level"></a><span data-ttu-id="95d21-245">Déduplication d’événements de message au niveau d’EventHandler</span><span class="sxs-lookup"><span data-stu-id="95d21-245">Deduplicating message events at the EventHandler level</span></span>

<span data-ttu-id="95d21-246">Un moyen de s’assurer qu’un événement n’est traité qu’une seule fois par un récepteur est d’implémenter une logique spécifique lors du traitement des événements de message dans les gestionnaires d’événements.</span><span class="sxs-lookup"><span data-stu-id="95d21-246">One way to make sure that an event is processed just once by any receiver is by implementing certain logic when processing the message events in event handlers.</span></span> <span data-ttu-id="95d21-247">Il s’agit de l’approche utilisée dans l’application eShopOnContainers, comme vous pouvez le voir dans le [code source de la classe UserCheckoutAcceptedIntegrationEventHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) lors de la réception d’un événement d’intégration UserCheckoutAcceptedIntegrationEvent.</span><span class="sxs-lookup"><span data-stu-id="95d21-247">For example, that is the approach used in the eShopOnContainers application, as you can see in the [source code of the UserCheckoutAcceptedIntegrationEventHandler class](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) when it receives an UserCheckoutAcceptedIntegrationEvent integration event.</span></span> <span data-ttu-id="95d21-248">(Dans le cas présent, nous wrappons la classe CreateOrderCommand avec un IdentifiedCommand, en utilisant eventMsg.RequestId comme identificateur, avant de l’envoyer au gestionnaire de commandes).</span><span class="sxs-lookup"><span data-stu-id="95d21-248">(In this case we wrap the CreateOrderCommand with an IdentifiedCommand, using the eventMsg.RequestId as an identifier, before sending it to the command handler).</span></span>

### <a name="deduplicating-messages-when-using-rabbitmq"></a><span data-ttu-id="95d21-249">Déduplication de messages lors de l’utilisation de RabbitMQ</span><span class="sxs-lookup"><span data-stu-id="95d21-249">Deduplicating messages when using RabbitMQ</span></span>

<span data-ttu-id="95d21-250">Lorsque des défaillances intermittentes du réseau se produisent, des messages peuvent être dupliqués et le récepteur des messages doit être prêt à gérer cette déduplication.</span><span class="sxs-lookup"><span data-stu-id="95d21-250">When intermittent network failures happen, messages can be duplicated, and the message receiver must be ready to handle these duplicated messages.</span></span> <span data-ttu-id="95d21-251">Si possible, les récepteurs doivent gérer les messages de manière idempotente, ce qui est mieux que de les gérer explicitement avec la déduplication.</span><span class="sxs-lookup"><span data-stu-id="95d21-251">If possible, receivers should handle messages in an idempotent way, which is better than explicitly handling them with deduplication.</span></span>

<span data-ttu-id="95d21-252">Conformément à la [documentation RabbitMQ](https://www.rabbitmq.com/reliability.html#consumer), si un message est remis à un utilisateur, puis est replacé dans la file d’attente (parce qu’il n’a pas été accepté avant la perte de la connexion de l’utilisateur, par exemple), RabbitMQ lui associe l’indicateur de redistribution lorsqu’il est remis à nouveau (au même utilisateur ou à un autre).</span><span class="sxs-lookup"><span data-stu-id="95d21-252">According to the [RabbitMQ documentation](https://www.rabbitmq.com/reliability.html#consumer), “If a message is delivered to a consumer and then requeued (because it was not acknowledged before the consumer connection dropped, for example) then RabbitMQ will set the redelivered flag on it when it is delivered again (whether to the same consumer or a different one).</span></span>

<span data-ttu-id="95d21-253">Si l’indicateur de redistribution est défini, le récepteur doit en tenir compte, car le message peut déjà avoir été traité.</span><span class="sxs-lookup"><span data-stu-id="95d21-253">If the “redelivered” flag is set, the receiver must take that into account, because the message might already have been processed.</span></span> <span data-ttu-id="95d21-254">Toutefois, cela n’est pas garanti. Le message peut ne jamais avoir atteint le récepteur après avoir quitté le répartiteur de messages, peut-être en raison de problèmes de réseau.</span><span class="sxs-lookup"><span data-stu-id="95d21-254">But that is not guaranteed; the message might never have reached the receiver after it left the message broker, perhaps because of network issues.</span></span> <span data-ttu-id="95d21-255">En revanche, si l’indicateur de redistribution n’est pas défini, il est garanti que le message n’a pas été envoyé plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="95d21-255">On the other hand, if the “redelivered” flag is not set, it is guaranteed that the message has not been sent more than once.</span></span> <span data-ttu-id="95d21-256">Par conséquent, le récepteur doit dédupliquer les messages ou les traiter de manière idempotente uniquement si l’indicateur de redistribution est défini dans le message.</span><span class="sxs-lookup"><span data-stu-id="95d21-256">Therefore, the receiver needs to deduplicate messages or process messages in an idempotent way only if the “redelivered” flag is set in the message.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="95d21-257">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="95d21-257">Additional resources</span></span>

- <span data-ttu-id="95d21-258">**Forked eShopOnContainers using NServiceBus (Particular Software)**  </span><span class="sxs-lookup"><span data-stu-id="95d21-258">**Forked eShopOnContainers using NServiceBus (Particular Software)** </span></span>\
    <https://go.particular.net/eShopOnContainers>

- <span data-ttu-id="95d21-259">**Event Driven Messaging** </span><span class="sxs-lookup"><span data-stu-id="95d21-259">**Event Driven Messaging** </span></span>\
    [http://soapatterns.org/design\_patterns/event\_driven\_messaging](http://soapatterns.org/design_patterns/event_driven_messaging)

- <span data-ttu-id="95d21-260">**Jimmy Bogard. Refactorisation vers la résilience : évaluation du couplage** </span><span class="sxs-lookup"><span data-stu-id="95d21-260">**Jimmy Bogard. Refactoring Towards Resilience: Evaluating Coupling** </span></span>\
    <https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/>

- <span data-ttu-id="95d21-261">**Publish-Subscribe channel** </span><span class="sxs-lookup"><span data-stu-id="95d21-261">**Publish-Subscribe channel** </span></span>\
    <https://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html>

- <span data-ttu-id="95d21-262">**Communication entre contextes délimités** </span><span class="sxs-lookup"><span data-stu-id="95d21-262">**Communicating Between Bounded Contexts** </span></span>\
    <https://docs.microsoft.com/previous-versions/msp-n-p/jj591572(v=pandp.10)>

- <span data-ttu-id="95d21-263">**Eventual Consistency** </span><span class="sxs-lookup"><span data-stu-id="95d21-263">**Eventual Consistency** </span></span>\
    [https://en.wikipedia.org/wiki/Eventual\_consistency](https://en.wikipedia.org/wiki/Eventual_consistency)

- <span data-ttu-id="95d21-264">**Philip Brown. Strategies for Integrating Bounded Contexts** </span><span class="sxs-lookup"><span data-stu-id="95d21-264">**Philip Brown. Strategies for Integrating Bounded Contexts** </span></span>\
    <https://www.culttt.com/2014/11/26/strategies-integrating-bounded-contexts/>

- <span data-ttu-id="95d21-265">**Chris Richardson. Developing Transactional Microservices Using Aggregates, Event Sourcing and CQRS - Part 2** </span><span class="sxs-lookup"><span data-stu-id="95d21-265">**Chris Richardson. Developing Transactional Microservices Using Aggregates, Event Sourcing and CQRS - Part 2** </span></span>\
    <https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson>

- <span data-ttu-id="95d21-266">**Chris Richardson. Event Sourcing pattern** </span><span class="sxs-lookup"><span data-stu-id="95d21-266">**Chris Richardson. Event Sourcing pattern** </span></span>\
    <https://microservices.io/patterns/data/event-sourcing.html>

- <span data-ttu-id="95d21-267">**Introducing Event Sourcing** </span><span class="sxs-lookup"><span data-stu-id="95d21-267">**Introducing Event Sourcing** </span></span>\
    <https://docs.microsoft.com/previous-versions/msp-n-p/jj591559(v=pandp.10)>

- <span data-ttu-id="95d21-268">**Base de données du magasin d’événements**.</span><span class="sxs-lookup"><span data-stu-id="95d21-268">**Event Store database**.</span></span> <span data-ttu-id="95d21-269">Site officiel.</span><span class="sxs-lookup"><span data-stu-id="95d21-269">Official site.</span></span> \
    <https://geteventstore.com/>

- <span data-ttu-id="95d21-270">**Patrick Nommensen. Event-Driven Data Management for Microservices** </span><span class="sxs-lookup"><span data-stu-id="95d21-270">**Patrick Nommensen. Event-Driven Data Management for Microservices** </span></span>\
    <https://dzone.com/articles/event-driven-data-management-for-microservices-1>

- <span data-ttu-id="95d21-271">**The CAP Theorem** </span><span class="sxs-lookup"><span data-stu-id="95d21-271">**The CAP Theorem** </span></span>\
    [https://en.wikipedia.org/wiki/CAP\_theorem](https://en.wikipedia.org/wiki/CAP_theorem)

- <span data-ttu-id="95d21-272">**What is CAP Theorem?**</span><span class="sxs-lookup"><span data-stu-id="95d21-272">**What is CAP Theorem?**</span></span> \
    <https://www.quora.com/What-Is-CAP-Theorem-1>

- <span data-ttu-id="95d21-273">**Data Consistency Primer** </span><span class="sxs-lookup"><span data-stu-id="95d21-273">**Data Consistency Primer** </span></span>\
    <https://docs.microsoft.com/previous-versions/msp-n-p/dn589800(v=pandp.10)>

- <span data-ttu-id="95d21-274">**Rick Saling. The CAP Theorem: Why “Everything is Different” with the Cloud and Internet** </span><span class="sxs-lookup"><span data-stu-id="95d21-274">**Rick Saling. The CAP Theorem: Why “Everything is Different” with the Cloud and Internet** </span></span>\
    <https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/>

- <span data-ttu-id="95d21-275">**Eric Brewer. CAP Twelve Years Later: How the "Rules" Have Changed** </span><span class="sxs-lookup"><span data-stu-id="95d21-275">**Eric Brewer. CAP Twelve Years Later: How the "Rules" Have Changed** </span></span>\
    <https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed>

- <span data-ttu-id="95d21-276">**Azure Service Bus. Brokered Messaging: Duplicate Detection**  </span><span class="sxs-lookup"><span data-stu-id="95d21-276">**Azure Service Bus. Brokered Messaging: Duplicate Detection**  </span></span>\
    <https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25>

- <span data-ttu-id="95d21-277">**Reliability Guide** (RabbitMQ documentation) </span><span class="sxs-lookup"><span data-stu-id="95d21-277">**Reliability Guide** (RabbitMQ documentation) </span></span>\
    [https://www.rabbitmq.com/reliability.html\#consumer](https://www.rabbitmq.com/reliability.html#consumer)

> [!div class="step-by-step"]
> <span data-ttu-id="95d21-278">[Précédent](rabbitmq-event-bus-development-test-environment.md)
> [Suivant](test-aspnet-core-services-web-apps.md)</span><span class="sxs-lookup"><span data-stu-id="95d21-278">[Previous](rabbitmq-event-bus-development-test-environment.md)
[Next](test-aspnet-core-services-web-apps.md)</span></span>
