---
title: Implémentation de lectures/requêtes dans un microservice CQRS
description: Architecture des microservices .NET pour les applications .NET conteneurisées | Comprendre l’implémentation du côté requêtes de CQRS sur le microservice Ordering dans eShopOnContainers avec Dapper.
ms.date: 10/08/2018
ms.openlocfilehash: 49f42a5035bab38f800f3ec5ea24b01fde0d2964
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988750"
---
# <a name="implement-readsqueries-in-a-cqrs-microservice"></a>Implémenter les lectures/requêtes dans un microservice CQRS

Pour les lectures/requêtes, le microservice Ordering (Commandes) de l’application de référence eShopOnContainers implémente les requêtes indépendamment du modèle DDD et de la zone transactionnelle. La raison principale en est que les demandes de requêtes et de transactions sont radicalement différentes. Les écritures exécutent des transactions qui doivent être conformes à la logique de domaine. En revanche, les requêtes sont idempotentes et peuvent être séparées des règles du domaine.

L’approche est simple, comme le montre la figure 7-3. L’interface API est implémentée par les contrôleurs d’API web à l’aide de n’importe quelle infrastructure, comme un micro-mappeur objet/relationnel (ORM) tel que Dapper, et en retournant des ViewModels dynamiques en fonction des besoins des applications d’interface utilisateur.

![Diagramme montrant des requêtes de haut niveau-côté dans CQRS simplifiés.](./media/cqrs-microservice-reads/simple-approach-cqrs-queries.png)

**Figure 7-3**. Approche la plus simple pour les requêtes dans un microservice CQRS

L’approche la plus simple pour le côté requêtes dans une approche CQRS simplifiée peut être implémentée en interrogeant simplement la base de données avec un micro-ORM comme Dapper, en retournant des ViewModels dynamiques. Les définitions de requête interrogent la base de données et retournent un ViewModel dynamique généré instantanément pour chaque requête. Étant donné que les requêtes sont idempotentes, elles ne changent pas les données, quel que soit le nombre d’exécutions d’une requête. Par conséquent, vous n’avez pas besoin d’être restreint par un modèle DDD utilisé du côté transactionnel, comme les agrégats et d’autres modèles. C’est pourquoi les requêtes sont séparées de la zone transactionnelle. Vous interrogez juste la base de données sur les données dont l’interface utilisateur a besoin et vous retournez un ViewModel dynamique qui n’a pas besoin d’être défini statiquement où que ce soit (aucune classe pour les ViewModels) excepté dans les instructions SQL elles-mêmes.

Dans la mesure où il s’agit d’une approche simple, le code nécessaire côté requêtes (comme le code utilisant un micro-ORM tel que [Dapper](https://github.com/StackExchange/Dapper)) peut être implémenté [dans le même projet d’API web](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs). La figure 7-4 illustre ceci. Les requêtes sont définies dans le projet de microservice **Ordering.API** dans la solution eShopOnContainers.

![Capture d’écran du dossier Requête du projet Ordering.API.](./media/cqrs-microservice-reads/ordering-api-queries-folder.png)

**Figure 7-4**. Requêtes dans le microservice de commandes dans eShopOnContainers

## <a name="use-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a>Utiliser des ViewModels spécifiquement conçus pour les applications clientes, indépendants des contraintes de modèle de domaine

Étant donné que les requêtes sont exécutées pour obtenir les données exigées par les applications clientes, le type retourné peut être spécifiquement conçu pour les clients, en fonction des données retournées par les requêtes. Ces modèles, ou objets de transfert de données (DTO), sont appelés ViewModels.

Les données retournées (ViewModel) peuvent être le résultat de données de plusieurs entités ou tables jointes à la base de données, ou même de plusieurs agrégats définis dans le modèle de domaine de la zone transactionnelle. Dans ce cas, étant donné que vous créez des requêtes indépendantes du modèle de domaine, les limites et contraintes des agrégats sont totalement ignorées et vous êtes libre d’interroger toute table et colonne dont vous avez besoin. Cette approche offre une grande souplesse et une grande productivité pour les développeurs qui créent ou mettent à jour les requêtes.

Les ViewModels peuvent être des types statiques définis dans des classes. Ils peuvent également être créés de manière dynamique en fonction des requêtes exécutées (tel qu’implémenté dans le microservice de commandes), ce qui représente une méthode très agile pour les développeurs.

## <a name="use-dapper-as-a-micro-orm-to-perform-queries"></a>Utiliser Dapper comme micro-ORM pour effectuer des requêtes

Vous pouvez utiliser n’importe quel micro-ORM, Entity Framework Core ou même ADO.NET standard pour exécuter des requêtes. Dans l’exemple d’application, Dapper a été sélectionné pour le microservice de commandes dans eShopOnContainers comme un bon exemple de micro-ORM courant. Vous pouvez exécuter des requêtes SQL standard avec de hautes performances, car il s’agit d’un framework très léger. Dapper vous permet d’écrire une requête SQL qui peut accéder à plusieurs tables et les joindre.

Dapper est un projet Open Source (initialement créé par Sam Saffron). Il fait partie des éléments essentiels utilisés dans [Stack Overflow](https://stackoverflow.com/). Pour utiliser Dapper, il vous suffit de l’installer par le biais du [package NuGet Dapper](https://www.nuget.org/packages/Dapper), comme illustré dans la figure suivante :

![Capture d’écran du paquet Dapper dans la vue des paquets NuGet.](./media/cqrs-microservice-reads/drapper-package-nuget.png)

Vous devez également ajouter une instruction using afin que votre code ait accès aux méthodes d’extension Dapper.

Quand vous utilisez Dapper dans votre code, vous utilisez directement la classe <xref:System.Data.SqlClient.SqlConnection> disponible dans l’espace de noms <xref:System.Data.SqlClient>. Avec la méthode QueryAsync et d’autres méthodes d’extension qui étendent la classe <xref:System.Data.SqlClient.SqlConnection>, vous pouvez simplement exécuter des requêtes de façon directe et performante.

## <a name="dynamic-versus-static-viewmodels"></a>ViewModels dynamiques et statiques

Quand des ViewModels sont retournés depuis le côté serveur à des applications clientes, vous pouvez considérer ces ViewModels comme des objets de transfert de données (DTO) qui peuvent être différents pour les entités de domaine internes de votre modèle d’entité, car les ViewModels contiennent les données comme l’application cliente le souhaite. Par conséquent, dans de nombreux cas, vous pouvez agréger des données provenant de plusieurs entités de domaine et composer les ViewModels précisément selon la façon dont l’application cliente a besoin de ces données.

Ces ViewModels, ou DTO, peuvent être définis explicitement (sous la forme de classes de conteneurs de données), comme la classe `OrderSummary` présentée ultérieurement dans un extrait de code. Vous pouvez également retourner simplement des ViewModels dynamiques ou des DTO dynamiques en fonction des attributs retournés par vos requêtes, sous la forme de type dynamique.

### <a name="viewmodel-as-dynamic-type"></a>ViewModel sous la forme d’un type dynamique

Comme illustré dans le code suivant, un `ViewModel` peut être retourné directement par les requêtes en retournant simplement un type *dynamique* qui, en interne, est basé sur les attributs retournés par une requête. Cela signifie que le sous-ensemble d’attributs à retourner est basé sur la requête elle-même. Par conséquent, si vous ajoutez une nouvelle colonne à la requête ou à la jointure, ces données sont dynamiquement ajoutées au `ViewModel` retourné.

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

Le point important à retenir est qu’en utilisant un type dynamique, la collection de données retournée est assemblée de manière dynamique sous la forme du ViewModel.

**Avantages :** Cette approche réduit la nécessité de modifier les classes ViewModel statiques quand vous mettez à jour la phrase SQL d’une requête. De ce fait, cette approche de conception est assez souple lors du codage, simple et peut évoluer rapidement en cas de changements futurs.

**Inconvénients :** à long terme, les types dynamiques peuvent nuire à la clarté et à la compatibilité d’un service avec les applications clientes. De plus, les middlewares (intergiciels) comme Swagger ne peuvent pas fournir le même niveau de documentation sur les types retournés si vous utilisez des types dynamiques.

### <a name="viewmodel-as-predefined-dto-classes"></a>ViewModel sous la forme de classes DTO prédéfinies

**Avantages**: Avoir des classes ViewModel statiques prédéfinis, comme des « contrats » basés sur des classes DTO explicites, est certainement meilleur pour les API publiques mais aussi pour les microservices à long terme, même s’ils ne sont utilisés que par la même application.

Si vous voulez spécifier des types de réponse pour Swagger, vous devez utiliser des classes DTO explicites comme type de retour. Par conséquent, les classes DTO prédéfinies vous permettent de fournir des informations plus détaillées à partir de Swagger. Cela améliore la documentation et la compatibilité d’une API lors de son utilisation.

**Inconvénient :** comme indiqué précédemment, lors de la mise à jour du code, certaines étapes supplémentaires sont nécessaires pour mettre à jour les classes DTO.

*Conseil basés sur notre expérience :* Dans les requêtes implémentées au niveau du microservice Ordering dans eShopOnContainers, nous avons commencé le développement en utilisant des ViewModels, car c’était très simple et agile pour les premières étapes du développement. Mais, une fois le développement stabilisé, nous avons choisi de refactoriser les API et d’utiliser des DTO statiques ou prédéfinis pour les ViewModels, car il est plus clair pour les consommateurs du microservice de connaître les types de DTO explicites, utilisés comme «contrats».

Dans l’exemple suivant, vous pouvez voir comment la requête retourne des données en utilisant une classe DTO de ViewModel explicite : la classe OrderSummary.

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

#### <a name="describe-response-types-of-web-apis"></a>Décrire les types de réponse des API web

Les développeurs qui consomment des API web et des microservices se soucient davantage de ce qui est retourné, plus spécifiquement par les types de réponse et les codes d’erreur (s’ils ne sont pas standard). Ceux-ci sont gérés dans les annotations de données et les commentaires XML.

Sans documentation appropriée dans l’interface utilisateur de Swagger, le consommateur n’a pas connaissance des types retournés ou des codes HTTP pouvant être retournés. Ce problème est résolu en ajoutant le <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType>, afin que Swashbuckle puisse générer des informations plus détaillées concernant les valeurs et le modèle de retour de l’API, comme montré dans le code suivant :

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

Toutefois, l’attribut `ProducesResponseType` ne peut pas utiliser dynamic comme type, mais exige d’utiliser des types explicites, comme le DTO de ViewModel `OrderSummary`, illustré dans l’exemple suivant :

```csharp
public class OrderSummary
{
    public int ordernumber { get; set; }
    public DateTime date { get; set; }
    public string status { get; set; }
    public double total { get; set; }
}
```

C’est une autre raison pour laquelle les types retournés explicites sont, à long terme, préférables aux types dynamiques. Quand vous utilisez l’attribut `ProducesResponseType`, vous pouvez également spécifier le résultat attendu en ce qui concerne les erreurs/codes HTTP possibles, comme 200, 400, etc.

Dans l’image suivante, vous pouvez voir comment l’interface utilisateur de Swagger affiche les informations ResponseType.

![Capture d’écran de la page de l’interface utilisateur Swagger pour l’API de commande.](./media/cqrs-microservice-reads/swagger-ordering-http-api.png)

**Figure 7-5**. Interface utilisateur de Swagger affichant les types de réponse et les codes d’état HTTP possibles à partir d’une API web

L’image ci-dessus présente des exemples de valeurs basés sur les types ViewModel, ainsi que les codes d’état HTTP qui peuvent être retournés.

## <a name="additional-resources"></a>Ressources supplémentaires

- **Dapper**  
 <https://github.com/StackExchange/dapper-dot-net>

- **Julie Lerman. Points de données - Dapper, Entity Framework et Hybrid Apps (article du magazine MSDN)**  
  <https://docs.microsoft.com/archive/msdn-magazine/2016/may/data-points-dapper-entity-framework-and-hybrid-apps>

- **ASP.NET Pages d’aide à l’API Web de base à l’aide de Swagger**  
  <https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger?tabs=visual-studio>

>[!div class="step-by-step"]
>[Suivant précédent](eshoponcontainers-cqrs-ddd-microservice.md)
>[Next](ddd-oriented-microservice.md)
