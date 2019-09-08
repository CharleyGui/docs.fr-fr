---
title: Applications multicouches LINQ to SQL avec ASP.NET
ms.date: 03/30/2017
ms.assetid: f6cc863a-d6a6-4281-ba8b-197c01cf6c6f
ms.openlocfilehash: 1770d84053b57e05d1a4e41919a3eb4122dc73a3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793035"
---
# <a name="linq-to-sql-n-tier-with-aspnet"></a>Applications multicouches LINQ to SQL avec ASP.NET
Dans les applications ASP.net qui [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]utilisent, vous utilisez <xref:System.Web.UI.WebControls.LinqDataSource> le contrôle serveur Web. Ce contrôle gère la plus grande part de la logique dont il doit disposer pour exécuter des requêtes sur [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], passer les données au navigateur, les récupérer et les soumettre à [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> qui met ensuite à jour la base de données. Vous configurez simplement le contrôle dans le balisage et le contrôle gère tous les transferts de données entre [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] et le navigateur. Étant donné que le contrôle gère les interactions avec la couche présentation [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] et gère la communication avec la couche données, votre principal objectif dans les applications multicouches ASP.net est l’écriture de votre logique métier personnalisée.  
  
 Pour plus d’informations `LINQDataSource`sur, consultez [vue d’ensemble du contrôle serveur Web LinqDataSource](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100)).  
  
## <a name="see-also"></a>Voir aussi

- [Applications multicouches et distantes avec LINQ to SQL](n-tier-and-remote-applications-with-linq-to-sql.md)
