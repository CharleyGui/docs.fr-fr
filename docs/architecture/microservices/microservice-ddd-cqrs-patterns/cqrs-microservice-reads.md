---
title: Implémentation de lectures/requêtes dans un microservice CQRS
description: Architecture des microservices .NET pour les applications .NET conteneurisées | Comprendre l’implémentation du côté requêtes de CQRS sur le microservice Ordering dans eShopOnContainers avec Dapper.
ms.date: 10/08/2018
ms.openlocfilehash: 41932122326cf4c49b9c9e2c344d2ac17da7466b
ms.sourcegitcommit: ae2e8a61a93c5cf3f0035c59e6b064fa2f812d14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89358893"
---
# <a name="implement-readsqueries-in-a-cqrs-microservice"></a><span data-ttu-id="bca5e-103">Implémenter les lectures/requêtes dans un microservice CQRS</span><span class="sxs-lookup"><span data-stu-id="bca5e-103">Implement reads/queries in a CQRS microservice</span></span>

<span data-ttu-id="bca5e-104">Pour les lectures/requêtes, le microservice Ordering (Commandes) de l’application de référence eShopOnContainers implémente les requêtes indépendamment du modèle DDD et de la zone transactionnelle.</span><span class="sxs-lookup"><span data-stu-id="bca5e-104">For reads/queries, the ordering microservice from the eShopOnContainers reference application implements the queries independently from the DDD model and transactional area.</span></span> <span data-ttu-id="bca5e-105">La raison principale en est que les demandes de requêtes et de transactions sont radicalement différentes.</span><span class="sxs-lookup"><span data-stu-id="bca5e-105">This was done primarily because the demands for queries and for transactions are drastically different.</span></span> <span data-ttu-id="bca5e-106">Les écritures exécutent des transactions qui doivent être conformes à la logique de domaine.</span><span class="sxs-lookup"><span data-stu-id="bca5e-106">Writes execute transactions that must be compliant with the domain logic.</span></span> <span data-ttu-id="bca5e-107">En revanche, les requêtes sont idempotentes et peuvent être séparées des règles du domaine.</span><span class="sxs-lookup"><span data-stu-id="bca5e-107">Queries, on the other hand, are idempotent and can be segregated from the domain rules.</span></span>

<span data-ttu-id="bca5e-108">L’approche est simple, comme le montre la figure 7-3.</span><span class="sxs-lookup"><span data-stu-id="bca5e-108">The approach is simple, as shown in Figure 7-3.</span></span> <span data-ttu-id="bca5e-109">L’interface API est implémentée par les contrôleurs d’API web à l’aide de n’importe quelle infrastructure, comme un micro-mappeur objet/relationnel (ORM) tel que Dapper, et en retournant des ViewModels dynamiques en fonction des besoins des applications d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="bca5e-109">The API interface is implemented by the Web API controllers using any infrastructure, such as a micro Object Relational Mapper (ORM) like Dapper, and returning dynamic ViewModels depending on the needs of the UI applications.</span></span>

![Diagramme montrant les requêtes de haut niveau, côté de la CQRS simplifiée.](./media/cqrs-microservice-reads/simple-approach-cqrs-queries.png)

<span data-ttu-id="bca5e-111">**Figure 7-3**.</span><span class="sxs-lookup"><span data-stu-id="bca5e-111">**Figure 7-3**.</span></span> <span data-ttu-id="bca5e-112">Approche la plus simple pour les requêtes dans un microservice CQRS</span><span class="sxs-lookup"><span data-stu-id="bca5e-112">The simplest approach for queries in a CQRS microservice</span></span>

<span data-ttu-id="bca5e-113">Il est possible d’implémenter l’approche la plus simple pour les requêtes dans une approche CQRS simplifiée en interrogeant la base de données avec un micro-ORM comme dapper, en renvoyant des ViewModels dynamiques.</span><span class="sxs-lookup"><span data-stu-id="bca5e-113">The simplest approach for the queries-side in a simplified CQRS approach can be implemented by querying the database with a Micro-ORM like Dapper, returning dynamic ViewModels.</span></span> <span data-ttu-id="bca5e-114">Les définitions de requête interrogent la base de données et retournent un ViewModel dynamique généré instantanément pour chaque requête.</span><span class="sxs-lookup"><span data-stu-id="bca5e-114">The query definitions query the database and return a dynamic ViewModel built on the fly for each query.</span></span> <span data-ttu-id="bca5e-115">Étant donné que les requêtes sont idempotentes, elles ne changent pas les données, quel que soit le nombre d’exécutions d’une requête.</span><span class="sxs-lookup"><span data-stu-id="bca5e-115">Since the queries are idempotent, they won't change the data no matter how many times you run a query.</span></span> <span data-ttu-id="bca5e-116">Par conséquent, vous n’avez pas besoin d’être restreint par un modèle DDD utilisé du côté transactionnel, comme les agrégats et d’autres modèles. C’est pourquoi les requêtes sont séparées de la zone transactionnelle.</span><span class="sxs-lookup"><span data-stu-id="bca5e-116">Therefore, you don't need to be restricted by any DDD pattern used in the transactional side, like aggregates and other patterns, and that is why queries are separated from the transactional area.</span></span> <span data-ttu-id="bca5e-117">Vous interrogez la base de données pour obtenir les données dont l’interface utilisateur a besoin et retourner un ViewModel dynamique qui n’a pas besoin d’être défini de manière statique en tout lieu (aucune classe pour le ViewModels), sauf dans les instructions SQL elles-mêmes.</span><span class="sxs-lookup"><span data-stu-id="bca5e-117">You query the database for the data that the UI needs and return a dynamic ViewModel that does not need to be statically defined anywhere (no classes for the ViewModels) except in the SQL statements themselves.</span></span>

<span data-ttu-id="bca5e-118">Dans la mesure où cette approche est simple, le code requis pour le côté des requêtes (par exemple, le code utilisant un micro ORM comme [dapper](https://github.com/StackExchange/Dapper)) peut être implémenté [dans le même projet d’API Web](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs).</span><span class="sxs-lookup"><span data-stu-id="bca5e-118">Since this approach is simple, the code required for the queries side (such as code using a micro ORM like [Dapper](https://github.com/StackExchange/Dapper)) can be implemented [within the same Web API project](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs).</span></span> <span data-ttu-id="bca5e-119">La figure 7-4 illustre ceci.</span><span class="sxs-lookup"><span data-stu-id="bca5e-119">Figure 7-4 shows this.</span></span> <span data-ttu-id="bca5e-120">Les requêtes sont définies dans le projet de microservice **Ordering.API** dans la solution eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="bca5e-120">The queries are defined in the **Ordering.API** microservice project within the eShopOnContainers solution.</span></span>

![Capture d’écran du dossier de requêtes du projet Ordering. API.](./media/cqrs-microservice-reads/ordering-api-queries-folder.png)

<span data-ttu-id="bca5e-122">**Figure 7-4**.</span><span class="sxs-lookup"><span data-stu-id="bca5e-122">**Figure 7-4**.</span></span> <span data-ttu-id="bca5e-123">Requêtes dans le microservice de commandes dans eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="bca5e-123">Queries in the Ordering microservice in eShopOnContainers</span></span>

## <a name="use-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a><span data-ttu-id="bca5e-124">Utiliser des ViewModels spécifiquement conçus pour les applications clientes, indépendants des contraintes de modèle de domaine</span><span class="sxs-lookup"><span data-stu-id="bca5e-124">Use ViewModels specifically made for client apps, independent from domain model constraints</span></span>

<span data-ttu-id="bca5e-125">Étant donné que les requêtes sont exécutées pour obtenir les données exigées par les applications clientes, le type retourné peut être spécifiquement conçu pour les clients, en fonction des données retournées par les requêtes.</span><span class="sxs-lookup"><span data-stu-id="bca5e-125">Since the queries are performed to obtain the data needed by the client applications, the returned type can be specifically made for the clients, based on the data returned by the queries.</span></span> <span data-ttu-id="bca5e-126">Ces modèles, ou objets de transfert de données (DTO), sont appelés ViewModels.</span><span class="sxs-lookup"><span data-stu-id="bca5e-126">These models, or Data Transfer Objects (DTOs), are called ViewModels.</span></span>

<span data-ttu-id="bca5e-127">Les données retournées (ViewModel) peuvent être le résultat de données de plusieurs entités ou tables jointes à la base de données, ou même de plusieurs agrégats définis dans le modèle de domaine de la zone transactionnelle.</span><span class="sxs-lookup"><span data-stu-id="bca5e-127">The returned data (ViewModel) can be the result of joining data from multiple entities or tables in the database, or even across multiple aggregates defined in the domain model for the transactional area.</span></span> <span data-ttu-id="bca5e-128">Dans ce cas, étant donné que vous créez des requêtes indépendantes du modèle de domaine, les limites et contraintes des agrégats sont ignorées et vous êtes libre d’interroger une table et une colonne dont vous pourriez avoir besoin.</span><span class="sxs-lookup"><span data-stu-id="bca5e-128">In this case, because you are creating queries independent of the domain model, the aggregates boundaries and constraints are ignored and you're free to query any table and column you might need.</span></span> <span data-ttu-id="bca5e-129">Cette approche offre une grande souplesse et une grande productivité pour les développeurs qui créent ou mettent à jour les requêtes.</span><span class="sxs-lookup"><span data-stu-id="bca5e-129">This approach provides great flexibility and productivity for the developers creating or updating the queries.</span></span>

<span data-ttu-id="bca5e-130">Les ViewModels peuvent être des types statiques définis dans des classes (tels qu’ils sont implémentés dans le microservice de commande).</span><span class="sxs-lookup"><span data-stu-id="bca5e-130">The ViewModels can be static types defined in classes (as is implemented in the ordering microservice).</span></span> <span data-ttu-id="bca5e-131">Ils peuvent être créés dynamiquement en fonction des requêtes effectuées, ce qui est très agile pour les développeurs.</span><span class="sxs-lookup"><span data-stu-id="bca5e-131">Or they can be created dynamically based on the queries performed, which is very agile for developers.</span></span>

## <a name="use-dapper-as-a-micro-orm-to-perform-queries"></a><span data-ttu-id="bca5e-132">Utiliser Dapper comme micro-ORM pour effectuer des requêtes</span><span class="sxs-lookup"><span data-stu-id="bca5e-132">Use Dapper as a micro ORM to perform queries</span></span>

<span data-ttu-id="bca5e-133">Vous pouvez utiliser n’importe quel micro-ORM, Entity Framework Core ou même ADO.NET standard pour exécuter des requêtes.</span><span class="sxs-lookup"><span data-stu-id="bca5e-133">You can use any micro ORM, Entity Framework Core, or even plain ADO.NET for querying.</span></span> <span data-ttu-id="bca5e-134">Dans l’exemple d’application, Dapper a été sélectionné pour le microservice de commandes dans eShopOnContainers comme un bon exemple de micro-ORM courant.</span><span class="sxs-lookup"><span data-stu-id="bca5e-134">In the sample application, Dapper was selected for the ordering microservice in eShopOnContainers as a good example of a popular micro ORM.</span></span> <span data-ttu-id="bca5e-135">Il peut exécuter des requêtes SQL brutes avec de bonnes performances, car il s’agit d’une infrastructure légère.</span><span class="sxs-lookup"><span data-stu-id="bca5e-135">It can run plain SQL queries with great performance, because it's a light framework.</span></span> <span data-ttu-id="bca5e-136">Dapper vous permet d’écrire une requête SQL qui peut accéder à plusieurs tables et les joindre.</span><span class="sxs-lookup"><span data-stu-id="bca5e-136">Using Dapper, you can write a SQL query that can access and join multiple tables.</span></span>

<span data-ttu-id="bca5e-137">Dapper est un projet Open Source (initialement créé par Sam Saffron). Il fait partie des éléments essentiels utilisés dans [Stack Overflow](https://stackoverflow.com/).</span><span class="sxs-lookup"><span data-stu-id="bca5e-137">Dapper is an open-source project (original created by Sam Saffron), and is part of the building blocks used in [Stack Overflow](https://stackoverflow.com/).</span></span> <span data-ttu-id="bca5e-138">Pour utiliser Dapper, il vous suffit de l’installer par le biais du [package NuGet Dapper](https://www.nuget.org/packages/Dapper), comme illustré dans la figure suivante :</span><span class="sxs-lookup"><span data-stu-id="bca5e-138">To use Dapper, you just need to install it through the [Dapper NuGet package](https://www.nuget.org/packages/Dapper), as shown in the following figure:</span></span>

![Capture d’écran du package dapper dans la vue packages NuGet.](./media/cqrs-microservice-reads/drapper-package-nuget.png)

<span data-ttu-id="bca5e-140">Vous devez également ajouter une `using` directive afin que votre code ait accès aux méthodes d’extension dapper.</span><span class="sxs-lookup"><span data-stu-id="bca5e-140">You also need to add a `using` directive so your code has access to the Dapper extension methods.</span></span>

<span data-ttu-id="bca5e-141">Quand vous utilisez Dapper dans votre code, vous utilisez directement la classe <xref:System.Data.SqlClient.SqlConnection> disponible dans l’espace de noms <xref:System.Data.SqlClient>.</span><span class="sxs-lookup"><span data-stu-id="bca5e-141">When you use Dapper in your code, you directly use the <xref:System.Data.SqlClient.SqlConnection> class available in the <xref:System.Data.SqlClient> namespace.</span></span> <span data-ttu-id="bca5e-142">À l’aide de la méthode QueryAsync et d’autres méthodes d’extension qui étendent la <xref:System.Data.SqlClient.SqlConnection> classe, vous pouvez exécuter des requêtes de façon simple et performante.</span><span class="sxs-lookup"><span data-stu-id="bca5e-142">Through the QueryAsync method and other extension methods that extend the <xref:System.Data.SqlClient.SqlConnection> class, you can run queries in a straightforward and performant way.</span></span>

## <a name="dynamic-versus-static-viewmodels"></a><span data-ttu-id="bca5e-143">ViewModels dynamiques et statiques</span><span class="sxs-lookup"><span data-stu-id="bca5e-143">Dynamic versus static ViewModels</span></span>

<span data-ttu-id="bca5e-144">Quand des ViewModels sont retournés depuis le côté serveur à des applications clientes, vous pouvez considérer ces ViewModels comme des objets de transfert de données (DTO) qui peuvent être différents pour les entités de domaine internes de votre modèle d’entité, car les ViewModels contiennent les données comme l’application cliente le souhaite.</span><span class="sxs-lookup"><span data-stu-id="bca5e-144">When returning ViewModels from the server-side to client apps, you can think about those ViewModels as DTOs (Data Transfer Objects) that can be different to the internal domain entities of your entity model because the ViewModels hold the data the way the client app needs.</span></span> <span data-ttu-id="bca5e-145">Par conséquent, dans de nombreux cas, vous pouvez agréger des données provenant de plusieurs entités de domaine et composer les ViewModels précisément selon la façon dont l’application cliente a besoin de ces données.</span><span class="sxs-lookup"><span data-stu-id="bca5e-145">Therefore, in many cases, you can aggregate data coming from multiple domain entities and compose the ViewModels precisely according to how the client app needs that data.</span></span>

<span data-ttu-id="bca5e-146">Ces ViewModels ou DTO peuvent être définis explicitement (en tant que classes de porteurs de données), comme la `OrderSummary` classe indiquée dans un extrait de code ultérieur.</span><span class="sxs-lookup"><span data-stu-id="bca5e-146">Those ViewModels or DTOs can be defined explicitly (as data holder classes), like the `OrderSummary` class shown in a later code snippet.</span></span> <span data-ttu-id="bca5e-147">Vous pouvez aussi simplement retourner des ViewModels dynamiques ou des DTO dynamiques en fonction des attributs retournés par vos requêtes sous forme de type dynamique.</span><span class="sxs-lookup"><span data-stu-id="bca5e-147">Or, you could just return dynamic ViewModels or dynamic DTOs based on the attributes returned by your queries as a dynamic type.</span></span>

### <a name="viewmodel-as-dynamic-type"></a><span data-ttu-id="bca5e-148">ViewModel sous la forme d’un type dynamique</span><span class="sxs-lookup"><span data-stu-id="bca5e-148">ViewModel as dynamic type</span></span>

<span data-ttu-id="bca5e-149">Comme illustré dans le code suivant, un `ViewModel` peut être retourné directement par les requêtes en retournant simplement un type *dynamique* qui, en interne, est basé sur les attributs retournés par une requête.</span><span class="sxs-lookup"><span data-stu-id="bca5e-149">As shown in the following code, a `ViewModel` can be directly returned by the queries by just returning a *dynamic* type that internally is based on the attributes returned by a query.</span></span> <span data-ttu-id="bca5e-150">Cela signifie que le sous-ensemble d’attributs à retourner est basé sur la requête elle-même.</span><span class="sxs-lookup"><span data-stu-id="bca5e-150">That means that the subset of attributes to be returned is based on the query itself.</span></span> <span data-ttu-id="bca5e-151">Par conséquent, si vous ajoutez une nouvelle colonne à la requête ou à la jointure, ces données sont dynamiquement ajoutées au `ViewModel` retourné.</span><span class="sxs-lookup"><span data-stu-id="bca5e-151">Therefore, if you add a new column to the query or join, that data is dynamically added to the returned `ViewModel`.</span></span>

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

<span data-ttu-id="bca5e-152">Le point important à retenir est qu’en utilisant un type dynamique, la collection de données retournée est assemblée de manière dynamique sous la forme du ViewModel.</span><span class="sxs-lookup"><span data-stu-id="bca5e-152">The important point is that by using a dynamic type, the returned collection of data is dynamically assembled as the ViewModel.</span></span>

<span data-ttu-id="bca5e-153">**Avantages :** Cette approche réduit la nécessité de modifier des classes ViewModel statiques chaque fois que vous mettez à jour la phrase SQL d’une requête, ce qui rend cette approche de conception agile quand vous codez, vous pouvez facilement et rapidement évoluer en ce qui concerne les futures modifications.</span><span class="sxs-lookup"><span data-stu-id="bca5e-153">**Pros:** This approach reduces the need to modify static ViewModel classes whenever you update the SQL sentence of a query, making this design approach agile when coding, straightforward, and quick to evolve in regard to future changes.</span></span>

<span data-ttu-id="bca5e-154">**Inconvénients :** à long terme, les types dynamiques peuvent nuire à la clarté et à la compatibilité d’un service avec les applications clientes.</span><span class="sxs-lookup"><span data-stu-id="bca5e-154">**Cons:** In the long term, dynamic types can negatively impact the clarity and the compatibility of a service with client apps.</span></span> <span data-ttu-id="bca5e-155">De plus, les middlewares (intergiciels) comme Swagger ne peuvent pas fournir le même niveau de documentation sur les types retournés si vous utilisez des types dynamiques.</span><span class="sxs-lookup"><span data-stu-id="bca5e-155">In addition, middleware software like Swashbuckle cannot provide the same level of documentation on returned types if using dynamic types.</span></span>

### <a name="viewmodel-as-predefined-dto-classes"></a><span data-ttu-id="bca5e-156">ViewModel sous la forme de classes DTO prédéfinies</span><span class="sxs-lookup"><span data-stu-id="bca5e-156">ViewModel as predefined DTO classes</span></span>

<span data-ttu-id="bca5e-157">**Avantages**: avoir des classes ViewModel statiques prédéfinies, telles que « Contracts » reposant sur des classes DTO explicites, est sans aucun doute mieux pour les API publiques, mais également pour les microservices à long terme, même s’ils sont utilisés uniquement par la même application.</span><span class="sxs-lookup"><span data-stu-id="bca5e-157">**Pros**: Having static, predefined ViewModel classes, like "contracts" based on explicit DTO classes, is definitely better for public APIs but also for long-term microservices, even if they are only used by the same application.</span></span>

<span data-ttu-id="bca5e-158">Si vous voulez spécifier des types de réponse pour Swagger, vous devez utiliser des classes DTO explicites comme type de retour.</span><span class="sxs-lookup"><span data-stu-id="bca5e-158">If you want to specify response types for Swagger, you need to use explicit DTO classes as the return type.</span></span> <span data-ttu-id="bca5e-159">Par conséquent, les classes DTO prédéfinies vous permettent de fournir des informations plus détaillées à partir de Swagger.</span><span class="sxs-lookup"><span data-stu-id="bca5e-159">Therefore, predefined DTO classes allow you to offer richer information from Swagger.</span></span> <span data-ttu-id="bca5e-160">Cela améliore la documentation et la compatibilité d’une API lors de son utilisation.</span><span class="sxs-lookup"><span data-stu-id="bca5e-160">That improves the API documentation and compatibility when consuming an API.</span></span>

<span data-ttu-id="bca5e-161">**Inconvénient :** comme indiqué précédemment, lors de la mise à jour du code, certaines étapes supplémentaires sont nécessaires pour mettre à jour les classes DTO.</span><span class="sxs-lookup"><span data-stu-id="bca5e-161">**Cons**: As mentioned earlier, when updating the code, it takes some more steps to update the DTO classes.</span></span>

<span data-ttu-id="bca5e-162">*Conseil basé sur notre expérience*: dans les requêtes implémentées au niveau du microservice de commande dans eShopOnContainers, nous avons commencé à développer à l’aide de ViewModels dynamiques, car il était simple et agile lors des premières étapes du développement.</span><span class="sxs-lookup"><span data-stu-id="bca5e-162">*Tip based on our experience*: In the queries implemented at the Ordering microservice in eShopOnContainers, we started developing by using dynamic ViewModels as it was straightforward and agile on the early development stages.</span></span> <span data-ttu-id="bca5e-163">Toutefois, une fois que le développement a été stabilisé, nous avons choisi de refactoriser les API et d’utiliser des DTO statiques ou prédéfinis pour le ViewModels, car il est plus clair pour les consommateurs du microservice de connaître les types DTO explicites, utilisés comme « contrats ».</span><span class="sxs-lookup"><span data-stu-id="bca5e-163">But, once the development was stabilized, we chose to refactor the APIs and use static or pre-defined DTOs for the ViewModels, because it is clearer for the microservice's consumers to know explicit DTO types, used as "contracts".</span></span>

<span data-ttu-id="bca5e-164">Dans l’exemple suivant, vous pouvez voir comment la requête retourne des données en utilisant une classe DTO de ViewModel explicite : la classe OrderSummary.</span><span class="sxs-lookup"><span data-stu-id="bca5e-164">In the following example, you can see how the query is returning data by using an explicit ViewModel DTO class: the OrderSummary class.</span></span>

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

#### <a name="describe-response-types-of-web-apis"></a><span data-ttu-id="bca5e-165">Décrire les types de réponse des API web</span><span class="sxs-lookup"><span data-stu-id="bca5e-165">Describe response types of Web APIs</span></span>

<span data-ttu-id="bca5e-166">Les développeurs qui utilisent des API Web et des microservices se préoccupent de ce qui est retourné, en particulier les types de réponse et les codes d’erreur (s’ils ne sont pas standard).</span><span class="sxs-lookup"><span data-stu-id="bca5e-166">Developers consuming web APIs and microservices are most concerned with what is returned—specifically response types and error codes (if not standard).</span></span> <span data-ttu-id="bca5e-167">Les types de réponse sont gérés dans les commentaires XML et les annotations de données.</span><span class="sxs-lookup"><span data-stu-id="bca5e-167">The response types are handled in the XML comments and data annotations.</span></span>

<span data-ttu-id="bca5e-168">Sans documentation appropriée dans l’interface utilisateur de Swagger, le consommateur n’a pas connaissance des types retournés ou des codes HTTP pouvant être retournés.</span><span class="sxs-lookup"><span data-stu-id="bca5e-168">Without proper documentation in the Swagger UI, the consumer lacks knowledge of what types are being returned or what HTTP codes can be returned.</span></span> <span data-ttu-id="bca5e-169">Ce problème est résolu en ajoutant le <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType>, afin que Swashbuckle puisse générer des informations plus détaillées concernant les valeurs et le modèle de retour de l’API, comme montré dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="bca5e-169">That problem is fixed by adding the <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType>, so Swashbuckle can generate richer information about the API return model and values, as shown in the following code:</span></span>

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

<span data-ttu-id="bca5e-170">Toutefois, l’attribut `ProducesResponseType` ne peut pas utiliser dynamic comme type, mais exige d’utiliser des types explicites, comme le DTO de ViewModel `OrderSummary`, illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="bca5e-170">However, the `ProducesResponseType` attribute cannot use dynamic as a type but requires to use explicit types, like the `OrderSummary` ViewModel DTO, shown in the following example:</span></span>

```csharp
public class OrderSummary
{
    public int ordernumber { get; set; }
    public DateTime date { get; set; }
    public string status { get; set; }
    public double total { get; set; }
}
```

<span data-ttu-id="bca5e-171">C’est une autre raison pour laquelle les types retournés explicites sont, à long terme, préférables aux types dynamiques.</span><span class="sxs-lookup"><span data-stu-id="bca5e-171">This is another reason why explicit returned types are better than dynamic types, in the long term.</span></span> <span data-ttu-id="bca5e-172">Quand vous utilisez l’attribut `ProducesResponseType`, vous pouvez également spécifier le résultat attendu en ce qui concerne les erreurs/codes HTTP possibles, comme 200, 400, etc.</span><span class="sxs-lookup"><span data-stu-id="bca5e-172">When using the `ProducesResponseType` attribute, you can also specify what is the expected outcome in regards possible HTTP errors/codes, like 200, 400, etc.</span></span>

<span data-ttu-id="bca5e-173">Dans l’image suivante, vous pouvez voir comment l’interface utilisateur de Swagger affiche les informations ResponseType.</span><span class="sxs-lookup"><span data-stu-id="bca5e-173">In the following image, you can see how Swagger UI shows the ResponseType information.</span></span>

![Capture d’écran de la page d’interface utilisateur Swagger pour l’API de tri.](./media/cqrs-microservice-reads/swagger-ordering-http-api.png)

<span data-ttu-id="bca5e-175">**Figure 7-5**.</span><span class="sxs-lookup"><span data-stu-id="bca5e-175">**Figure 7-5**.</span></span> <span data-ttu-id="bca5e-176">Interface utilisateur de Swagger affichant les types de réponse et les codes d’état HTTP possibles à partir d’une API web</span><span class="sxs-lookup"><span data-stu-id="bca5e-176">Swagger UI showing response types and possible HTTP status codes from a Web API</span></span>

<span data-ttu-id="bca5e-177">L’image montre des exemples de valeurs en fonction des types ViewModel et des codes d’état HTTP possibles qui peuvent être retournés.</span><span class="sxs-lookup"><span data-stu-id="bca5e-177">The image shows some example values based on the ViewModel types and the possible HTTP status codes that can be returned.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="bca5e-178">Ressources complémentaires</span><span class="sxs-lookup"><span data-stu-id="bca5e-178">Additional resources</span></span>

- <span data-ttu-id="bca5e-179">**Dapper**</span><span class="sxs-lookup"><span data-stu-id="bca5e-179">**Dapper**</span></span>  
 <https://github.com/StackExchange/dapper-dot-net>

- <span data-ttu-id="bca5e-180">**Julie Lerman. Points de données-dapper, Entity Framework et applications hybrides (article MSDN Magazine)**</span><span class="sxs-lookup"><span data-stu-id="bca5e-180">**Julie Lerman. Data Points - Dapper, Entity Framework and Hybrid Apps (MSDN magazine article)**</span></span>  
  <https://docs.microsoft.com/archive/msdn-magazine/2016/may/data-points-dapper-entity-framework-and-hybrid-apps>

- <span data-ttu-id="bca5e-181">**ASP.NET Core les pages d’aide de l’API Web à l’aide de Swagger**</span><span class="sxs-lookup"><span data-stu-id="bca5e-181">**ASP.NET Core Web API Help Pages using Swagger**</span></span>  
  <https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger?tabs=visual-studio>

>[!div class="step-by-step"]
><span data-ttu-id="bca5e-182">[Précédent](eshoponcontainers-cqrs-ddd-microservice.md) 
> [Suivant](ddd-oriented-microservice.md)</span><span class="sxs-lookup"><span data-stu-id="bca5e-182">[Previous](eshoponcontainers-cqrs-ddd-microservice.md)
[Next](ddd-oriented-microservice.md)</span></span>
