---
title: SqlDependency dans une application ASP.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ff226ce3-f6b5-47a1-8d22-dc78b67e07f5
ms.openlocfilehash: 2ec9415f63151443d5008fbce471fabeb89cdb91
ms.sourcegitcommit: 1e8382d0ce8b5515864f8fbb178b9fd692a7503f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2020
ms.locfileid: "89656169"
---
# <a name="sqldependency-in-an-aspnet-application"></a>SqlDependency dans une application ASP.NET
L’exemple de cette section montre comment utiliser <xref:System.Data.SqlClient.SqlDependency> indirectement en tirant parti de l’objet ASP.NET <xref:System.Web.Caching.SqlCacheDependency>. L’objet <xref:System.Web.Caching.SqlCacheDependency> utilise une <xref:System.Data.SqlClient.SqlDependency> pour écouter les notifications et mettre correctement à jour le cache.  
  
> [!NOTE]
> L’exemple de code suppose que vous avez activé les notifications de requête en exécutant les scripts dans [activation des notifications de requête](enabling-query-notifications.md).  
  
## <a name="about-the-sample-application"></a>À propose de l'exemple d'application  
 L’exemple d’application utilise une page web ASP.NET unique pour afficher les références des produits extraites de la base de données SQL Server **AdventureWorks** dans un contrôle <xref:System.Web.UI.WebControls.GridView>. Lors du chargement de la page, le code écrit l’heure actuelle dans un contrôle <xref:System.Web.UI.WebControls.Label>. Il définit ensuite un objet <xref:System.Web.Caching.SqlCacheDependency> puis des propriétés sur l’objet <xref:System.Web.Caching.Cache> pour stocker les données du cache pendant trois minutes maximum. Le code se connecte ensuite à la base de données et récupère les données. Lorsque la page est chargée et que l’application est en cours d’exécution, ASP.NET récupère les données du cache, que vous pouvez vérifier en notant que l’heure sur la page n’est pas modifiée. Si les données analysées sont modifiées, ASP.NET invalide le cache et remplit à nouveau le contrôle de `GridView` avec les données actualisées, en mettant à jour l’heure affichée dans le contrôle `Label`.  
  
## <a name="creating-the-sample-application"></a>Création de l'exemple d'application  
 Procédez comme suit pour créer et exécuter l’exemple d’application :  
  
1. Créez un site web ASP.NET.  
  
2. Ajoutez un <xref:System.Web.UI.WebControls.Label> et un contrôle <xref:System.Web.UI.WebControls.GridView> à la page Default.aspx.  
  
3. Ouvrez le module de classe de la page et ajoutez les directives suivantes :  
  
    ```vb  
    Option Strict On  
    Option Explicit On  
  
    Imports System.Data.SqlClient  
    ```  
  
    ```csharp  
    using System.Data.SqlClient;  
    using System.Web.Caching;  
    ```  
  
4. Ajoutez le code suivant dans l’événement `Page_Load` de la page :  
  
     [!code-csharp[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#1)]
     [!code-vb[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#1)]  
  
5. Ajoutez deux méthodes d'assistance, `GetConnectionString` et `GetSQL`. La chaîne de connexion définie utilise une sécurité intégrée. Vous devez vérifier que le compte que vous utilisez dispose des autorisations de base de données nécessaires et que les notifications sont activées dans l’exemple de base de données, **AdventureWorks**.
  
     [!code-csharp[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#2)]
     [!code-vb[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#2)]  
  
### <a name="testing-the-application"></a>Test de l’application  
 L’application met en cache les données affichées sur le formulaire Web et l’actualise toutes les trois minutes en l’absence d’activité. Si une modification est apportée à la base de données, le cache est actualisé immédiatement. Exécutez l’application à partir de Visual Studio, qui charge la page dans le navigateur. L’heure d’actualisation du cache affichée indique à quel moment le cache a été actualisé pour la dernière fois. Attendez trois minutes, puis actualisez la page, provoquant ainsi l’exécution d’un événement de publication (postback). Notez que l’heure affichée sur la page a changé. Si vous actualisez la page en moins de trois minutes, l’heure affichée sur la page reste la même.  
  
 Mettez à jour les données dans la base de données en utilisant une commande Transact-SQL UPDATE et en actualisant la page. L’heure affichée indique maintenant que le cache a été actualisé avec les nouvelles données de la base de données. Notez que même si le cache est mis à jour, l’heure affichée sur la page n’est pas modifiée tant qu’un événement de publication ne se produit pas.  

## <a name="distributed-cache-synchronization-using-sql-dependency"></a>Synchronisation du cache distribué à l’aide de la dépendance SQL

Certains des caches distribués tiers tels que [NCache](https://www.alachisoft.com/ncache) prennent en charge la synchronisation de la base de données SQL et du cache à l’aide de la [dépendance SQL](https://www.alachisoft.com/resources/docs/ncache/prog-guide/sql-dependency.html). Pour plus d’informations et pour obtenir un exemple d’implémentation de code source, consultez [exemple de dépendance SQL de cache distribué](https://github.com/Alachisoft/NCache-Samples/tree/master/dotnet/Dependencies/SQLDependency).

## <a name="see-also"></a>Voir aussi

- [Notifications de requêtes dans SQL Server](query-notifications-in-sql-server.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
