---
title: SqlDependency dans une application ASP.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ff226ce3-f6b5-47a1-8d22-dc78b67e07f5
ms.openlocfilehash: 7c982550533cb6d8547ab2ce78ad2e814d07857f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91184792"
---
# <a name="sqldependency-in-an-aspnet-application"></a><span data-ttu-id="3eacf-102">SqlDependency dans une application ASP.NET</span><span class="sxs-lookup"><span data-stu-id="3eacf-102">SqlDependency in an ASP.NET Application</span></span>

<span data-ttu-id="3eacf-103">L’exemple de cette section montre comment utiliser <xref:System.Data.SqlClient.SqlDependency> indirectement en tirant parti de l’objet ASP.NET <xref:System.Web.Caching.SqlCacheDependency>.</span><span class="sxs-lookup"><span data-stu-id="3eacf-103">The example in this section shows how to use <xref:System.Data.SqlClient.SqlDependency> indirectly by leveraging the ASP.NET <xref:System.Web.Caching.SqlCacheDependency> object.</span></span> <span data-ttu-id="3eacf-104">L’objet <xref:System.Web.Caching.SqlCacheDependency> utilise une <xref:System.Data.SqlClient.SqlDependency> pour écouter les notifications et mettre correctement à jour le cache.</span><span class="sxs-lookup"><span data-stu-id="3eacf-104">The <xref:System.Web.Caching.SqlCacheDependency> object uses a <xref:System.Data.SqlClient.SqlDependency> to listen for notifications and correctly update the cache.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3eacf-105">L’exemple de code suppose que vous avez activé les notifications de requête en exécutant les scripts dans [activation des notifications de requête](enabling-query-notifications.md).</span><span class="sxs-lookup"><span data-stu-id="3eacf-105">The sample code assumes that you have enabled query notifications by executing the scripts in [Enabling Query Notifications](enabling-query-notifications.md).</span></span>  
  
## <a name="about-the-sample-application"></a><span data-ttu-id="3eacf-106">À propose de l'exemple d'application</span><span class="sxs-lookup"><span data-stu-id="3eacf-106">About the Sample Application</span></span>  

 <span data-ttu-id="3eacf-107">L’exemple d’application utilise une page web ASP.NET unique pour afficher les références des produits extraites de la base de données SQL Server **AdventureWorks** dans un contrôle <xref:System.Web.UI.WebControls.GridView>.</span><span class="sxs-lookup"><span data-stu-id="3eacf-107">The sample application uses a single ASP.NET Web page to display product information from the **AdventureWorks** SQL Server database in a <xref:System.Web.UI.WebControls.GridView> control.</span></span> <span data-ttu-id="3eacf-108">Lors du chargement de la page, le code écrit l’heure actuelle dans un contrôle <xref:System.Web.UI.WebControls.Label>.</span><span class="sxs-lookup"><span data-stu-id="3eacf-108">When the page loads, the code writes the current time to a <xref:System.Web.UI.WebControls.Label> control.</span></span> <span data-ttu-id="3eacf-109">Il définit ensuite un objet <xref:System.Web.Caching.SqlCacheDependency> puis des propriétés sur l’objet <xref:System.Web.Caching.Cache> pour stocker les données du cache pendant trois minutes maximum.</span><span class="sxs-lookup"><span data-stu-id="3eacf-109">It then defines a <xref:System.Web.Caching.SqlCacheDependency> object and sets properties on the <xref:System.Web.Caching.Cache> object to store the cache data for up to three minutes.</span></span> <span data-ttu-id="3eacf-110">Le code se connecte ensuite à la base de données et récupère les données.</span><span class="sxs-lookup"><span data-stu-id="3eacf-110">The code then connects to the database and retrieves the data.</span></span> <span data-ttu-id="3eacf-111">Lorsque la page est chargée et que l’application est en cours d’exécution, ASP.NET récupère les données du cache, que vous pouvez vérifier en notant que l’heure sur la page n’est pas modifiée.</span><span class="sxs-lookup"><span data-stu-id="3eacf-111">When the page is loaded and the application is running ASP.NET will retrieve data from the cache, which you can verify by noting that the time on the page does not change.</span></span> <span data-ttu-id="3eacf-112">Si les données analysées sont modifiées, ASP.NET invalide le cache et remplit à nouveau le contrôle de `GridView` avec les données actualisées, en mettant à jour l’heure affichée dans le contrôle `Label`.</span><span class="sxs-lookup"><span data-stu-id="3eacf-112">If the data being monitored changes, ASP.NET invalidates the cache and repopulate the `GridView` control with fresh data, updating the time displayed in the `Label` control.</span></span>  
  
## <a name="creating-the-sample-application"></a><span data-ttu-id="3eacf-113">Création de l'exemple d'application</span><span class="sxs-lookup"><span data-stu-id="3eacf-113">Creating the Sample Application</span></span>  

 <span data-ttu-id="3eacf-114">Procédez comme suit pour créer et exécuter l’exemple d’application :</span><span class="sxs-lookup"><span data-stu-id="3eacf-114">Follow these steps to create and run the sample application:</span></span>  
  
1. <span data-ttu-id="3eacf-115">Créez un site web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="3eacf-115">Create a new ASP.NET Web site.</span></span>  
  
2. <span data-ttu-id="3eacf-116">Ajoutez un <xref:System.Web.UI.WebControls.Label> et un contrôle <xref:System.Web.UI.WebControls.GridView> à la page Default.aspx.</span><span class="sxs-lookup"><span data-stu-id="3eacf-116">Add a <xref:System.Web.UI.WebControls.Label> and a <xref:System.Web.UI.WebControls.GridView> control to the Default.aspx page.</span></span>  
  
3. <span data-ttu-id="3eacf-117">Ouvrez le module de classe de la page et ajoutez les directives suivantes :</span><span class="sxs-lookup"><span data-stu-id="3eacf-117">Open the page's class module and add the following directives:</span></span>  
  
    ```vb  
    Option Strict On  
    Option Explicit On  
  
    Imports System.Data.SqlClient  
    ```  
  
    ```csharp  
    using System.Data.SqlClient;  
    using System.Web.Caching;  
    ```  
  
4. <span data-ttu-id="3eacf-118">Ajoutez le code suivant dans l’événement `Page_Load` de la page :</span><span class="sxs-lookup"><span data-stu-id="3eacf-118">Add the following code in the page's `Page_Load` event:</span></span>  
  
     [!code-csharp[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#1)]
     [!code-vb[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#1)]  
  
5. <span data-ttu-id="3eacf-119">Ajoutez deux méthodes d'assistance, `GetConnectionString` et `GetSQL`.</span><span class="sxs-lookup"><span data-stu-id="3eacf-119">Add two helper methods, `GetConnectionString` and `GetSQL`.</span></span> <span data-ttu-id="3eacf-120">La chaîne de connexion définie utilise une sécurité intégrée.</span><span class="sxs-lookup"><span data-stu-id="3eacf-120">The connection string defined uses integrated security.</span></span> <span data-ttu-id="3eacf-121">Vous devez vérifier que le compte que vous utilisez dispose des autorisations de base de données nécessaires et que les notifications sont activées dans l’exemple de base de données, **AdventureWorks**.</span><span class="sxs-lookup"><span data-stu-id="3eacf-121">You will need to verify that the account you are using has the necessary database permissions and that the sample database, **AdventureWorks**, has notifications enabled.</span></span>
  
     [!code-csharp[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#2)]
     [!code-vb[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#2)]  
  
### <a name="testing-the-application"></a><span data-ttu-id="3eacf-122">Test de l’application</span><span class="sxs-lookup"><span data-stu-id="3eacf-122">Testing the Application</span></span>  

 <span data-ttu-id="3eacf-123">L’application met en cache les données affichées sur le formulaire Web et l’actualise toutes les trois minutes en l’absence d’activité.</span><span class="sxs-lookup"><span data-stu-id="3eacf-123">The application caches the data displayed on the Web form and refreshes it every three minutes if there is no activity.</span></span> <span data-ttu-id="3eacf-124">Si une modification est apportée à la base de données, le cache est actualisé immédiatement.</span><span class="sxs-lookup"><span data-stu-id="3eacf-124">If a change occurs to the database, the cache is refreshed immediately.</span></span> <span data-ttu-id="3eacf-125">Exécutez l’application à partir de Visual Studio, qui charge la page dans le navigateur.</span><span class="sxs-lookup"><span data-stu-id="3eacf-125">Run the application from Visual Studio, which loads the page into the browser.</span></span> <span data-ttu-id="3eacf-126">L’heure d’actualisation du cache affichée indique à quel moment le cache a été actualisé pour la dernière fois.</span><span class="sxs-lookup"><span data-stu-id="3eacf-126">The cache refresh time displayed indicates when the cache was last refreshed.</span></span> <span data-ttu-id="3eacf-127">Attendez trois minutes, puis actualisez la page, provoquant ainsi l’exécution d’un événement de publication (postback).</span><span class="sxs-lookup"><span data-stu-id="3eacf-127">Wait three minutes, and then refresh the page, causing a postback event to occur.</span></span> <span data-ttu-id="3eacf-128">Notez que l’heure affichée sur la page a changé.</span><span class="sxs-lookup"><span data-stu-id="3eacf-128">Note that the time displayed on the page has changed.</span></span> <span data-ttu-id="3eacf-129">Si vous actualisez la page en moins de trois minutes, l’heure affichée sur la page reste la même.</span><span class="sxs-lookup"><span data-stu-id="3eacf-129">If you refresh the page in less than three minutes, the time displayed on the page will remain the same.</span></span>  
  
 <span data-ttu-id="3eacf-130">Mettez à jour les données dans la base de données en utilisant une commande Transact-SQL UPDATE et en actualisant la page.</span><span class="sxs-lookup"><span data-stu-id="3eacf-130">Now update the data in the database, using a Transact-SQL UPDATE command and refresh the page.</span></span> <span data-ttu-id="3eacf-131">L’heure affichée indique maintenant que le cache a été actualisé avec les nouvelles données de la base de données.</span><span class="sxs-lookup"><span data-stu-id="3eacf-131">The time displayed now indicates that the cache was refreshed with the new data from the database.</span></span> <span data-ttu-id="3eacf-132">Notez que même si le cache est mis à jour, l’heure affichée sur la page n’est pas modifiée tant qu’un événement de publication ne se produit pas.</span><span class="sxs-lookup"><span data-stu-id="3eacf-132">Note that although the cache is updated, the time displayed on the page does not change until a postback event occurs.</span></span>  

## <a name="distributed-cache-synchronization-using-sql-dependency"></a><span data-ttu-id="3eacf-133">Synchronisation du cache distribué à l’aide de la dépendance SQL</span><span class="sxs-lookup"><span data-stu-id="3eacf-133">Distributed cache synchronization using SQL Dependency</span></span>

<span data-ttu-id="3eacf-134">Certains des caches distribués tiers tels que [NCache](https://www.alachisoft.com/ncache) prennent en charge la synchronisation de la base de données SQL et du cache à l’aide de la [dépendance SQL](https://www.alachisoft.com/resources/docs/ncache/prog-guide/sql-dependency.html).</span><span class="sxs-lookup"><span data-stu-id="3eacf-134">Some of the third-party distributed caches such as [NCache](https://www.alachisoft.com/ncache) provide support to synchronize the SQL database and cache using [SQL Dependency](https://www.alachisoft.com/resources/docs/ncache/prog-guide/sql-dependency.html).</span></span> <span data-ttu-id="3eacf-135">Pour plus d’informations et pour obtenir un exemple d’implémentation de code source, consultez [exemple de dépendance SQL de cache distribué](https://github.com/Alachisoft/NCache-Samples/tree/master/dotnet/Dependencies/SQLDependency).</span><span class="sxs-lookup"><span data-stu-id="3eacf-135">For more information and an example source code implementation, see [Distributed cache SQL Dependency sample](https://github.com/Alachisoft/NCache-Samples/tree/master/dotnet/Dependencies/SQLDependency).</span></span>

## <a name="see-also"></a><span data-ttu-id="3eacf-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3eacf-136">See also</span></span>

- [<span data-ttu-id="3eacf-137">Notifications de requêtes dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="3eacf-137">Query Notifications in SQL Server</span></span>](query-notifications-in-sql-server.md)
- [<span data-ttu-id="3eacf-138">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="3eacf-138">ADO.NET Overview</span></span>](../ado-net-overview.md)
