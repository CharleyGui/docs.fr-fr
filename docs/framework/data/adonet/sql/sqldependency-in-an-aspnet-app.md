---
title: SqlDependency dans une application ASP.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ff226ce3-f6b5-47a1-8d22-dc78b67e07f5
ms.openlocfilehash: a93cb9da44985fa29a4975875564b384117ce76f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938452"
---
# <a name="sqldependency-in-an-aspnet-application"></a>SqlDependency dans une application ASP.NET
L'exemple de cette section montre comment utiliser <xref:System.Data.SqlClient.SqlDependency> indirectement en tirant parti de l'objet <xref:System.Web.Caching.SqlCacheDependency> ASP.NET. L'objet <xref:System.Web.Caching.SqlCacheDependency> utilise un objet <xref:System.Data.SqlClient.SqlDependency> pour écouter les notifications et mettre correctement à jour le cache.  
  
> [!NOTE]
> L’exemple de code suppose que vous avez activé les notifications de requête en exécutant les scripts dans [activation des notifications de requête](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md).  
  
## <a name="about-the-sample-application"></a>À propose de l'exemple d'application  
 L’exemple d’application utilise une page Web ASP.net unique pour afficher les informations sur les produits de la base <xref:System.Web.UI.WebControls.GridView> de données AdventureWorks SQL Server dans un contrôle. Lorsque la page se charge, le code écrit l'heure actuelle dans un contrôle <xref:System.Web.UI.WebControls.Label>. Ensuite, elle définit un objet <xref:System.Web.Caching.SqlCacheDependency> et les propriétés de l'objet <xref:System.Web.Caching.Cache> pour stocker les données du cache pendant trois minutes au maximum. Le code se connecte ensuite à la base de données et récupère les données. Une fois que la page est chargée et que l'application s'exécute, ASP.NET récupère les données dans le cache, ce que vous pouvez vérifier en notant que l'heure indiquée sur la page ne change pas. Si les données surveillées sont modifiées, ASP.NET invalide le cache et remplit de nouveau le contrôle `GridView` avec les données actualisées, ce qui met à jour l'heure affichée dans le contrôle `Label`.  
  
## <a name="creating-the-sample-application"></a>Création de l'exemple d'application  
 Procédez comme suit pour créer et exécuter l'exemple d'application :  
  
1. Créez un site Web ASP.NET.  
  
2. Ajoutez un contrôle <xref:System.Web.UI.WebControls.Label> et un contrôle <xref:System.Web.UI.WebControls.GridView> à la page Default.aspx.  
  
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
  
4. Ajoutez le code suivant dans l'événement `Page_Load` de la page :  
  
     [!code-csharp[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#1)]
     [!code-vb[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#1)]  
  
5. Ajoutez deux méthodes d'assistance, `GetConnectionString` et `GetSQL`. La chaîne de connexion définie utilise une sécurité intégrée. Vous devez vérifier que le compte que vous utilisez dispose des autorisations de base de données nécessaires et que les notifications sont activées pour l’exemple de base de données **AdventureWorks**.
  
     [!code-csharp[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#2)]
     [!code-vb[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#2)]  
  
### <a name="testing-the-application"></a>Test de l'application  
 L'application met en cache les données affichées sur le formulaire Web et l'actualise toutes les trois minutes en cas d'inactivité. En cas de modification de la base de données, le cache est immédiatement actualisé. Exécutez l'application à partir de Visual Studio, ce qui charge la page dans le navigateur. L'heure d'actualisation du cache affichée indique la dernière actualisation du cache. Attendez trois minutes, puis actualisez la page. Un événement de publication se produit alors. Notez que l'heure affichée sur la page a changé. Si vous actualisez la page avant trois minutes, l'heure affichée sur la page restera la même.  
  
 Mettez à jour les données dans la base de données en utilisant une commande Transact-SQL UPDATE, puis actualisez la page. L'heure affichée indique maintenant que le cache a été actualisé avec les nouvelles données de la base de données. Notez que même si le cache est mis à jour, l'heure affichée sur le page n'est pas modifiée tant qu'un événement de publication ne s'est pas produit.  
  
## <a name="see-also"></a>Voir aussi

- [Notifications de requête dans SQL Server](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)
- [Fournisseurs managés ADO.NET et centre de développement DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
