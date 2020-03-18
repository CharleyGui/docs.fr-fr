---
title: Implémentation de lectures/requêtes dans un microservice CQRS
description: Architecture des microservices .NET pour les applications .NET conteneurisées | Comprendre l’implémentation du côté requêtes de CQRS sur le microservice Ordering dans eShopOnContainers avec Dapper.
ms.date: 10/08/2018
ms.openlocfilehash: 235b0e471a17e2a37a883a111cf499b7837f3ea1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73972085"
---
# <a name="implement-readsqueries-in-a-cqrs-microservice"></a><span data-ttu-id="c016d-103">Implémenter les lectures/requêtes dans un microservice CQRS</span><span class="sxs-lookup"><span data-stu-id="c016d-103">Implement reads/queries in a CQRS microservice</span></span>

<span data-ttu-id="c016d-104">Pour les lectures/requêtes, le microservice Ordering (Commandes) de l’application de référence eShopOnContainers implémente les requêtes indépendamment du modèle DDD et de la zone transactionnelle.</span><span class="sxs-lookup"><span data-stu-id="c016d-104">For reads/queries, the ordering microservice from the eShopOnContainers reference application implements the queries independently from the DDD model and transactional area.</span></span> <span data-ttu-id="c016d-105">La raison principale en est que les demandes de requêtes et de transactions sont radicalement différentes.</span><span class="sxs-lookup"><span data-stu-id="c016d-105">This was done primarily because the demands for queries and for transactions are drastically different.</span></span> <span data-ttu-id="c016d-106">Les écritures exécutent des transactions qui doivent être conformes à la logique de domaine.</span><span class="sxs-lookup"><span data-stu-id="c016d-106">Writes execute transactions that must be compliant with the domain logic.</span></span> <span data-ttu-id="c016d-107">En revanche, les requêtes sont idempotentes et peuvent être séparées des règles du domaine.</span><span class="sxs-lookup"><span data-stu-id="c016d-107">Queries, on the other hand, are idempotent and can be segregated from the domain rules.</span></span>

<span data-ttu-id="c016d-108">L’approche est simple, comme le montre la figure 7-3.</span><span class="sxs-lookup"><span data-stu-id="c016d-108">The approach is simple, as shown in Figure 7-3.</span></span> <span data-ttu-id="c016d-109">L’interface API est implémentée par les contrôleurs d’API web à l’aide de n’importe quelle infrastructure, comme un micro-mappeur objet/relationnel (ORM) tel que Dapper, et en retournant des ViewModels dynamiques en fonction des besoins des applications d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c016d-109">The API interface is implemented by the Web API controllers using any infrastructure, such as a micro Object Relational Mapper (ORM) like Dapper, and returning dynamic ViewModels depending on the needs of the UI applications.</span></span>

![Diagramme montrant des requêtes de haut niveau-côté dans CQRS simplifiés.](./media/cqrs-microservice-reads/simple-approach-cqrs-queries.png)

<span data-ttu-id="c016d-111">**Figure 7-3**.</span><span class="sxs-lookup"><span data-stu-id="c016d-111">**Figure 7-3**.</span></span> <span data-ttu-id="c016d-112">Approche la plus simple pour les requêtes dans un microservice CQRS</span><span class="sxs-lookup"><span data-stu-id="c016d-112">The simplest approach for queries in a CQRS microservice</span></span>

<span data-ttu-id="c016d-113">L’approche la plus simple pour le côté requêtes dans une approche CQRS simplifiée peut être implémentée en interrogeant simplement la base de données avec un micro-ORM comme Dapper, en retournant des ViewModels dynamiques.</span><span class="sxs-lookup"><span data-stu-id="c016d-113">The simplest approach for the queries-side in a simplified CQRS approach can be implemented by just querying the database with a Micro-ORM like Dapper, returning dynamic ViewModels.</span></span> <span data-ttu-id="c016d-114">Les définitions de requête interrogent la base de données et retournent un ViewModel dynamique généré instantanément pour chaque requête.</span><span class="sxs-lookup"><span data-stu-id="c016d-114">The query definitions query the database and return a dynamic ViewModel built on the fly for each query.</span></span> <span data-ttu-id="c016d-115">Étant donné que les requêtes sont idempotentes, elles ne changent pas les données, quel que soit le nombre d’exécutions d’une requête.</span><span class="sxs-lookup"><span data-stu-id="c016d-115">Since the queries are idempotent, they won't change the data no matter how many times you run a query.</span></span> <span data-ttu-id="c016d-116">Par conséquent, vous n’avez pas besoin d’être restreint par un modèle DDD utilisé du côté transactionnel, comme les agrégats et d’autres modèles. C’est pourquoi les requêtes sont séparées de la zone transactionnelle.</span><span class="sxs-lookup"><span data-stu-id="c016d-116">Therefore, you don't need to be restricted by any DDD pattern used in the transactional side, like aggregates and other patterns, and that is why queries are separated from the transactional area.</span></span> <span data-ttu-id="c016d-117">Vous interrogez juste la base de données sur les données dont l’interface utilisateur a besoin et vous retournez un ViewModel dynamique qui n’a pas besoin d’être défini statiquement où que ce soit (aucune classe pour les ViewModels) excepté dans les instructions SQL elles-mêmes.</span><span class="sxs-lookup"><span data-stu-id="c016d-117">You simply query the database for the data that the UI needs and return a dynamic ViewModel that does not need to be statically defined anywhere (no classes for the ViewModels) except in the SQL statements themselves.</span></span>

<span data-ttu-id="c016d-118">Dans la mesure où il s’agit d’une approche simple, le code nécessaire côté requêtes (comme le code utilisant un micro-ORM tel que [Dapper](https://github.com/StackExchange/Dapper)) peut être implémenté [dans le même projet d’API web](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs).</span><span class="sxs-lookup"><span data-stu-id="c016d-118">Since this is a simple approach, the code required for the queries side (such as code using a micro ORM like [Dapper](https://github.com/StackExchange/Dapper)) can be implemented [within the same Web API project](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs).</span></span> <span data-ttu-id="c016d-119">La figure 7-4 illustre ceci.</span><span class="sxs-lookup"><span data-stu-id="c016d-119">Figure 7-4 shows this.</span></span> <span data-ttu-id="c016d-120">Les requêtes sont définies dans le projet de microservice **Ordering.API** dans la solution eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="c016d-120">The queries are defined in the **Ordering.API** microservice project within the eShopOnContainers solution.</span></span>

![Capture d’écran du dossier Requête du projet Ordering.API.](./media/cqrs-microservice-reads/ordering-api-queries-folder.png)

<span data-ttu-id="c016d-122">**Figure 7-4**.</span><span class="sxs-lookup"><span data-stu-id="c016d-122">**Figure 7-4**.</span></span> <span data-ttu-id="c016d-123">Requêtes dans le microservice de commandes dans eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="c016d-123">Queries in the Ordering microservice in eShopOnContainers</span></span>

## <a name="use-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a><span data-ttu-id="c016d-124">Utiliser des ViewModels spécifiquement conçus pour les applications clientes, indépendants des contraintes de modèle de domaine</span><span class="sxs-lookup"><span data-stu-id="c016d-124">Use ViewModels specifically made for client apps, independent from domain model constraints</span></span>

<span data-ttu-id="c016d-125">Étant donné que les requêtes sont exécutées pour obtenir les données exigées par les applications clientes, le type retourné peut être spécifiquement conçu pour les clients, en fonction des données retournées par les requêtes.</span><span class="sxs-lookup"><span data-stu-id="c016d-125">Since the queries are performed to obtain the data needed by the client applications, the returned type can be specifically made for the clients, based on the data returned by the queries.</span></span> <span data-ttu-id="c016d-126">Ces modèles, ou objets de transfert de données (DTO), sont appelés ViewModels.</span><span class="sxs-lookup"><span data-stu-id="c016d-126">These models, or Data Transfer Objects (DTOs), are called ViewModels.</span></span>

<span data-ttu-id="c016d-127">Les données retournées (ViewModel) peuvent être le résultat de données de plusieurs entités ou tables jointes à la base de données, ou même de plusieurs agrégats définis dans le modèle de domaine de la zone transactionnelle.</span><span class="sxs-lookup"><span data-stu-id="c016d-127">The returned data (ViewModel) can be the result of joining data from multiple entities or tables in the database, or even across multiple aggregates defined in the domain model for the transactional area.</span></span> <span data-ttu-id="c016d-128">Dans ce cas, étant donné que vous créez des requêtes indépendantes du modèle de domaine, les limites et contraintes des agrégats sont totalement ignorées et vous êtes libre d’interroger toute table et colonne dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="c016d-128">In this case, because you are creating queries independent of the domain model, the aggregates boundaries and constraints are completely ignored and you're free to query any table and column you might need.</span></span> <span data-ttu-id="c016d-129">Cette approche offre une grande souplesse et une grande productivité pour les développeurs qui créent ou mettent à jour les requêtes.</span><span class="sxs-lookup"><span data-stu-id="c016d-129">This approach provides great flexibility and productivity for the developers creating or updating the queries.</span></span>

<span data-ttu-id="c016d-130">Les ViewModels peuvent être des types statiques définis dans des classes.</span><span class="sxs-lookup"><span data-stu-id="c016d-130">The ViewModels can be static types defined in classes.</span></span> <span data-ttu-id="c016d-131">Ils peuvent également être créés de manière dynamique en fonction des requêtes exécutées (tel qu’implémenté dans le microservice de commandes), ce qui représente une méthode très agile pour les développeurs.</span><span class="sxs-lookup"><span data-stu-id="c016d-131">Or they can be created dynamically based on the queries performed (as is implemented in the ordering microservice), which is very agile for developers.</span></span>

## <a name="use-dapper-as-a-micro-orm-to-perform-queries"></a><span data-ttu-id="c016d-132">Utiliser Dapper comme micro-ORM pour effectuer des requêtes</span><span class="sxs-lookup"><span data-stu-id="c016d-132">Use Dapper as a micro ORM to perform queries</span></span>

<span data-ttu-id="c016d-133">Vous pouvez utiliser n’importe quel micro-ORM, Entity Framework Core ou même ADO.NET standard pour exécuter des requêtes.</span><span class="sxs-lookup"><span data-stu-id="c016d-133">You can use any micro ORM, Entity Framework Core, or even plain ADO.NET for querying.</span></span> <span data-ttu-id="c016d-134">Dans l’exemple d’application, Dapper a été sélectionné pour le microservice de commandes dans eShopOnContainers comme un bon exemple de micro-ORM courant.</span><span class="sxs-lookup"><span data-stu-id="c016d-134">In the sample application, Dapper was selected for the ordering microservice in eShopOnContainers as a good example of a popular micro ORM.</span></span> <span data-ttu-id="c016d-135">Vous pouvez exécuter des requêtes SQL standard avec de hautes performances, car il s’agit d’un framework très léger.</span><span class="sxs-lookup"><span data-stu-id="c016d-135">It can run plain SQL queries with great performance, because it's a very light framework.</span></span> <span data-ttu-id="c016d-136">Dapper vous permet d’écrire une requête SQL qui peut accéder à plusieurs tables et les joindre.</span><span class="sxs-lookup"><span data-stu-id="c016d-136">Using Dapper, you can write a SQL query that can access and join multiple tables.</span></span>

<span data-ttu-id="c016d-137">Dapper est un projet Open Source (initialement créé par Sam Saffron). Il fait partie des éléments essentiels utilisés dans [Stack Overflow](https://stackoverflow.com/).</span><span class="sxs-lookup"><span data-stu-id="c016d-137">Dapper is an open-source project (original created by Sam Saffron), and is part of the building blocks used in [Stack Overflow](https://stackoverflow.com/).</span></span> <span data-ttu-id="c016d-138">Pour utiliser Dapper, il vous suffit de l’installer par le biais du [package NuGet Dapper](https://www.nuget.org/packages/Dapper), comme illustré dans la figure suivante :</span><span class="sxs-lookup"><span data-stu-id="c016d-138">To use Dapper, you just need to install it through the [Dapper NuGet package](https://www.nuget.org/packages/Dapper), as shown in the following figure:</span></span>

![Capture d’écran du paquet Dapper dans la vue des paquets NuGet.](./media/cqrs-microservice-reads/drapper-package-nuget.png)

<span data-ttu-id="c016d-140">Vous devez également ajouter une instruction using afin que votre code ait accès aux méthodes d’extension Dapper.</span><span class="sxs-lookup"><span data-stu-id="c016d-140">You also need to add a using statement so your code has access to the Dapper extension methods.</span></span>

<span data-ttu-id="c016d-141">Quand vous utilisez Dapper dans votre code, vous utilisez directement la classe <xref:System.Data.SqlClient.SqlConnection> disponible dans l’espace de noms <xref:System.Data.SqlClient>.</span><span class="sxs-lookup"><span data-stu-id="c016d-141">When you use Dapper in your code, you directly use the <xref:System.Data.SqlClient.SqlConnection> class available in the <xref:System.Data.SqlClient> namespace.</span></span> <span data-ttu-id="c016d-142">Avec la méthode QueryAsync et d’autres méthodes d’extension qui étendent la classe <xref:System.Data.SqlClient.SqlConnection>, vous pouvez simplement exécuter des requêtes de façon directe et performante.</span><span class="sxs-lookup"><span data-stu-id="c016d-142">Through the QueryAsync method and other extension methods that extend the <xref:System.Data.SqlClient.SqlConnection> class, you can simply run queries in a straightforward and performant way.</span></span>

## <a name="dynamic-versus-static-viewmodels"></a><span data-ttu-id="c016d-143">ViewModels dynamiques et statiques</span><span class="sxs-lookup"><span data-stu-id="c016d-143">Dynamic versus static ViewModels</span></span>

<span data-ttu-id="c016d-144">Quand des ViewModels sont retournés depuis le côté serveur à des applications clientes, vous pouvez considérer ces ViewModels comme des objets de transfert de données (DTO) qui peuvent être différents pour les entités de domaine internes de votre modèle d’entité, car les ViewModels contiennent les données comme l’application cliente le souhaite.</span><span class="sxs-lookup"><span data-stu-id="c016d-144">When returning ViewModels from the server-side to client apps, you can think about those ViewModels as DTOs (Data Transfer Objects) that can be different to the internal domain entities of your entity model because the ViewModels hold the data the way the client app needs.</span></span> <span data-ttu-id="c016d-145">Par conséquent, dans de nombreux cas, vous pouvez agréger des données provenant de plusieurs entités de domaine et composer les ViewModels précisément selon la façon dont l’application cliente a besoin de ces données.</span><span class="sxs-lookup"><span data-stu-id="c016d-145">Therefore, in many cases, you can aggregate data coming from multiple domain entities and compose the ViewModels precisely according to how the client app needs that data.</span></span>

<span data-ttu-id="c016d-146">Ces ViewModels, ou DTO, peuvent être définis explicitement (sous la forme de classes de conteneurs de données), comme la classe `OrderSummary` présentée ultérieurement dans un extrait de code. Vous pouvez également retourner simplement des ViewModels dynamiques ou des DTO dynamiques en fonction des attributs retournés par vos requêtes, sous la forme de type dynamique.</span><span class="sxs-lookup"><span data-stu-id="c016d-146">Those ViewModels or DTOs can be defined explicitly (as data holder classes) like the `OrderSummary` class shown in a later code snippet, or you could just return dynamic ViewModels or dynamic DTOs simply based on the attributes returned by your queries, as a dynamic type.</span></span>

### <a name="viewmodel-as-dynamic-type"></a><span data-ttu-id="c016d-147">ViewModel sous la forme d’un type dynamique</span><span class="sxs-lookup"><span data-stu-id="c016d-147">ViewModel as dynamic type</span></span>

<span data-ttu-id="c016d-148">Comme illustré dans le code suivant, un `ViewModel` peut être retourné directement par les requêtes en retournant simplement un type *dynamique* qui, en interne, est basé sur les attributs retournés par une requête.</span><span class="sxs-lookup"><span data-stu-id="c016d-148">As shown in the following code, a `ViewModel` can be directly returned by the queries by just returning a *dynamic* type that internally is based on the attributes returned by a query.</span></span> <span data-ttu-id="c016d-149">Cela signifie que le sous-ensemble d’attributs à retourner est basé sur la requête elle-même.</span><span class="sxs-lookup"><span data-stu-id="c016d-149">That means that the subset of attributes to be returned is based on the query itself.</span></span> <span data-ttu-id="c016d-150">Par conséquent, si vous ajoutez une nouvelle colonne à la requête ou à la jointure, ces données sont dynamiquement ajoutées au `ViewModel` retourné.</span><span class="sxs-lookup"><span data-stu-id="c016d-150">Therefore, if you add a new column to the query or join, that data is dynamically added to the returned `ViewModel`.</span></span>

```csharp
using Dapper;
using Microsoft.Extensions.Configuration;
using System.Data.SqlClient;
using System.Threading.Tasks;
using System.Dynamic;
using System.Collections.Generic;

public class OrderQueries : IOrderQueries
{
    public async Task<IEnumerable<dynamic>> GetOrdersAsync()
    {
        using (var connection = new SqlConnection(_connectionString))
        {
            connection.Open();
            return await connection.QueryAsync<dynamic>(
                @"SELECT o.[Id] as ordernumber,
                o.[OrderDate] as [date],os.[Name] as [status],
                SUM(oi.units*oi.unitprice) as total
                FROM [ordering].[Orders] o
                LEFT JOIN[ordering].[orderitems] oi ON o.Id = oi.orderid
                LEFT JOIN[ordering].[orderstatus] os on o.OrderStatusId = os.Id
                GROUP BY o.[Id], o.[OrderDate], os.[Name]");
        }
    }
}
```

<span data-ttu-id="c016d-151">Le point important à retenir est qu’en utilisant un type dynamique, la collection de données retournée est assemblée de manière dynamique sous la forme du ViewModel.</span><span class="sxs-lookup"><span data-stu-id="c016d-151">The important point is that by using a dynamic type, the returned collection of data is dynamically assembled as the ViewModel.</span></span>

<span data-ttu-id="c016d-152">**Avantages :** Cette approche réduit la nécessité de modifier les classes ViewModel statiques quand vous mettez à jour la phrase SQL d’une requête. De ce fait, cette approche de conception est assez souple lors du codage, simple et peut évoluer rapidement en cas de changements futurs.</span><span class="sxs-lookup"><span data-stu-id="c016d-152">**Pros:** This approach reduces the need to modify static ViewModel classes whenever you update the SQL sentence of a query, making this design approach pretty agile when coding, straightforward, and quick to evolve in regard to future changes.</span></span>

<span data-ttu-id="c016d-153">**Inconvénients :** à long terme, les types dynamiques peuvent nuire à la clarté et à la compatibilité d’un service avec les applications clientes.</span><span class="sxs-lookup"><span data-stu-id="c016d-153">**Cons:** In the long term, dynamic types can negatively impact the clarity and the compatibility of a service with client apps.</span></span> <span data-ttu-id="c016d-154">De plus, les middlewares (intergiciels) comme Swagger ne peuvent pas fournir le même niveau de documentation sur les types retournés si vous utilisez des types dynamiques.</span><span class="sxs-lookup"><span data-stu-id="c016d-154">In addition, middleware software like Swashbuckle cannot provide the same level of documentation on returned types if using dynamic types.</span></span>

### <a name="viewmodel-as-predefined-dto-classes"></a><span data-ttu-id="c016d-155">ViewModel sous la forme de classes DTO prédéfinies</span><span class="sxs-lookup"><span data-stu-id="c016d-155">ViewModel as predefined DTO classes</span></span>

<span data-ttu-id="c016d-156">**Avantages :** le fait d’avoir des classes ViewModel prédéfinies statiques, comme des « contrats » basés sur des classes DTO explicites, est définitivement meilleur pour les API publiques, mais également pour les microservices à long terme, même s’ils sont utilisés uniquement par la même application.</span><span class="sxs-lookup"><span data-stu-id="c016d-156">**Pros**: Having static predefined ViewModel classes, like “contracts” based on explicit DTO classes, is definitely better for public APIs but also for long term microservices, even if they are only used by the same application.</span></span>

<span data-ttu-id="c016d-157">Si vous voulez spécifier des types de réponse pour Swagger, vous devez utiliser des classes DTO explicites comme type de retour.</span><span class="sxs-lookup"><span data-stu-id="c016d-157">If you want to specify response types for Swagger, you need to use explicit DTO classes as the return type.</span></span> <span data-ttu-id="c016d-158">Par conséquent, les classes DTO prédéfinies vous permettent de fournir des informations plus détaillées à partir de Swagger.</span><span class="sxs-lookup"><span data-stu-id="c016d-158">Therefore, predefined DTO classes allow you to offer richer information from Swagger.</span></span> <span data-ttu-id="c016d-159">Cela améliore la documentation et la compatibilité d’une API lors de son utilisation.</span><span class="sxs-lookup"><span data-stu-id="c016d-159">That improves the API documentation and compatibility when consuming an API.</span></span>

<span data-ttu-id="c016d-160">**Inconvénient :** comme indiqué précédemment, lors de la mise à jour du code, certaines étapes supplémentaires sont nécessaires pour mettre à jour les classes DTO.</span><span class="sxs-lookup"><span data-stu-id="c016d-160">**Cons**: As mentioned earlier, when updating the code, it takes some more steps to update the DTO classes.</span></span>

<span data-ttu-id="c016d-161">*Conseil basés sur notre expérience :* Dans les requêtes implémentées au niveau du microservice Ordering dans eShopOnContainers, nous avons commencé le développement en utilisant des ViewModels, car c’était très simple et agile pour les premières étapes du développement.</span><span class="sxs-lookup"><span data-stu-id="c016d-161">*Tip based on our experience*: In the queries implemented at the Ordering microservice in eShopOnContainers, we started developing by using dynamic ViewModels as it was very straightforward and agile on the early development stages.</span></span> <span data-ttu-id="c016d-162">Toutefois, une fois le développement stabilisé, nous avons choisi de refactoriser les API et d’utiliser des DTO statiques ou prédéfinis pour les ViewModels, car il est plus clair pour les consommateurs du microservice de connaître les types de DTO explicites, utilisés comme « contrats ».</span><span class="sxs-lookup"><span data-stu-id="c016d-162">But, once the development was stabilized, we chose to refactor the APIs and use static or pre-defined DTOs for the ViewModels, because it is clearer for the microservice’s consumers to know explicit DTO types, used as "contracts".</span></span>

<span data-ttu-id="c016d-163">Dans l’exemple suivant, vous pouvez voir comment la requête retourne des données en utilisant une classe DTO de ViewModel explicite : la classe OrderSummary.</span><span class="sxs-lookup"><span data-stu-id="c016d-163">In the following example, you can see how the query is returning data by using an explicit ViewModel DTO class: the OrderSummary class.</span></span>

```csharp
using Dapper;
using Microsoft.Extensions.Configuration;
using System.Data.SqlClient;
using System.Threading.Tasks;
using System.Dynamic;
using System.Collections.Generic;

public class OrderQueries : IOrderQueries
{
  public async Task<IEnumerable<OrderSummary>> GetOrdersAsync()
    {
        using (var connection = new SqlConnection(_connectionString))
        {
            connection.Open();
            return await connection.QueryAsync<OrderSummary>(
                  @"SELECT o.[Id] as ordernumber,
                  o.[OrderDate] as [date],os.[Name] as [status],
                  SUM(oi.units*oi.unitprice) as total
                  FROM [ordering].[Orders] o
                  LEFT JOIN[ordering].[orderitems] oi ON  o.Id = oi.orderid
                  LEFT JOIN[ordering].[orderstatus] os on o.OrderStatusId = os.Id
                  GROUP BY o.[Id], o.[OrderDate], os.[Name]
                  ORDER BY o.[Id]");
        }
    }
}
```

#### <a name="describe-response-types-of-web-apis"></a><span data-ttu-id="c016d-164">Décrire les types de réponse des API web</span><span class="sxs-lookup"><span data-stu-id="c016d-164">Describe response types of Web APIs</span></span>

<span data-ttu-id="c016d-165">Les développeurs qui consomment des API web et des microservices se soucient davantage de ce qui est retourné, plus spécifiquement par les types de réponse et les codes d’erreur (s’ils ne sont pas standard).</span><span class="sxs-lookup"><span data-stu-id="c016d-165">Developers consuming web APIs and microservices are most concerned with what is returned — specifically response types and error codes (if not standard).</span></span> <span data-ttu-id="c016d-166">Ceux-ci sont gérés dans les annotations de données et les commentaires XML.</span><span class="sxs-lookup"><span data-stu-id="c016d-166">These are handled in the XML comments and data annotations.</span></span>

<span data-ttu-id="c016d-167">Sans documentation appropriée dans l’interface utilisateur de Swagger, le consommateur n’a pas connaissance des types retournés ou des codes HTTP pouvant être retournés.</span><span class="sxs-lookup"><span data-stu-id="c016d-167">Without proper documentation in the Swagger UI, the consumer lacks knowledge of what types are being returned or what HTTP codes can be returned.</span></span> <span data-ttu-id="c016d-168">Ce problème est résolu en ajoutant le <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType>, afin que Swashbuckle puisse générer des informations plus détaillées concernant les valeurs et le modèle de retour de l’API, comme montré dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="c016d-168">That problem is fixed by adding the <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType>, so Swashbuckle can generate richer information about the API return model and values, as shown in the following code:</span></span>

```csharp
namespace Microsoft.eShopOnContainers.Services.Ordering.API.Controllers
{
    [Route("api/v1/[controller]")]
    [Authorize]
    public class OrdersController : Controller
    {
        //Additional code...
        [Route("")]
        [HttpGet]
        [ProducesResponseType(typeof(IEnumerable<OrderSummary>),
            (int)HttpStatusCode.OK)]
        public async Task<IActionResult> GetOrders()
        {
            var userid = _identityService.GetUserIdentity();
            var orders = await _orderQueries
                .GetOrdersFromUserAsync(Guid.Parse(userid));
            return Ok(orders);
        }
    }
}
```

<span data-ttu-id="c016d-169">Toutefois, l’attribut `ProducesResponseType` ne peut pas utiliser dynamic comme type, mais exige d’utiliser des types explicites, comme le DTO de ViewModel `OrderSummary`, illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="c016d-169">However, the `ProducesResponseType` attribute cannot use dynamic as a type but requires to use explicit types, like the `OrderSummary` ViewModel DTO, shown in the following example:</span></span>

```csharp
public class OrderSummary
{
    public int ordernumber { get; set; }
    public DateTime date { get; set; }
    public string status { get; set; }
    public double total { get; set; }
}
```

<span data-ttu-id="c016d-170">C’est une autre raison pour laquelle les types retournés explicites sont, à long terme, préférables aux types dynamiques.</span><span class="sxs-lookup"><span data-stu-id="c016d-170">This is another reason why explicit returned types are better than dynamic types, in the long term.</span></span> <span data-ttu-id="c016d-171">Quand vous utilisez l’attribut `ProducesResponseType`, vous pouvez également spécifier le résultat attendu en ce qui concerne les erreurs/codes HTTP possibles, comme 200, 400, etc.</span><span class="sxs-lookup"><span data-stu-id="c016d-171">When using the `ProducesResponseType` attribute, you can also specify what is the expected outcome in regards possible HTTP errors/codes, like 200, 400, etc.</span></span>

<span data-ttu-id="c016d-172">Dans l’image suivante, vous pouvez voir comment l’interface utilisateur de Swagger affiche les informations ResponseType.</span><span class="sxs-lookup"><span data-stu-id="c016d-172">In the following image, you can see how Swagger UI shows the ResponseType information.</span></span>

![Capture d’écran de la page de l’interface utilisateur Swagger pour l’API de commande.](./media/cqrs-microservice-reads/swagger-ordering-http-api.png)

<span data-ttu-id="c016d-174">**Figure 7-5**.</span><span class="sxs-lookup"><span data-stu-id="c016d-174">**Figure 7-5**.</span></span> <span data-ttu-id="c016d-175">Interface utilisateur de Swagger affichant les types de réponse et les codes d’état HTTP possibles à partir d’une API web</span><span class="sxs-lookup"><span data-stu-id="c016d-175">Swagger UI showing response types and possible HTTP status codes from a Web API</span></span>

<span data-ttu-id="c016d-176">L’image ci-dessus présente des exemples de valeurs basés sur les types ViewModel, ainsi que les codes d’état HTTP qui peuvent être retournés.</span><span class="sxs-lookup"><span data-stu-id="c016d-176">You can see in the image above some example values based on the ViewModel types plus the possible HTTP status codes that can be returned.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="c016d-177">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="c016d-177">Additional resources</span></span>

- <span data-ttu-id="c016d-178">**Dapper**</span><span class="sxs-lookup"><span data-stu-id="c016d-178">**Dapper**</span></span>  
 <https://github.com/StackExchange/dapper-dot-net>

- <span data-ttu-id="c016d-179">**Julie Lerman. Points de données - Dapper, Entity Framework et Hybrid Apps (article du magazine MSDN)**</span><span class="sxs-lookup"><span data-stu-id="c016d-179">**Julie Lerman. Data Points - Dapper, Entity Framework and Hybrid Apps (MSDN magazine article)**</span></span>  
  <https://docs.microsoft.com/archive/msdn-magazine/2016/may/data-points-dapper-entity-framework-and-hybrid-apps>

- <span data-ttu-id="c016d-180">**ASP.NET Pages d’aide à l’API Web de base à l’aide de Swagger**</span><span class="sxs-lookup"><span data-stu-id="c016d-180">**ASP.NET Core Web API Help Pages using Swagger**</span></span>  
  <https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger?tabs=visual-studio>

>[!div class="step-by-step"]
><span data-ttu-id="c016d-181">[Suivant précédent](eshoponcontainers-cqrs-ddd-microservice.md)
>[Next](ddd-oriented-microservice.md)</span><span class="sxs-lookup"><span data-stu-id="c016d-181">[Previous](eshoponcontainers-cqrs-ddd-microservice.md)
[Next](ddd-oriented-microservice.md)</span></span>
