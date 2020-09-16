---
title: Applications multicouches LINQ to SQL avec ASP.NET
ms.date: 03/30/2017
ms.assetid: f6cc863a-d6a6-4281-ba8b-197c01cf6c6f
ms.openlocfilehash: 1af7f0d78f16e25c1ae7bf563c6abfb3b77f6183
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559224"
---
# <a name="linq-to-sql-n-tier-with-aspnet"></a>Applications multicouches LINQ to SQL avec ASP.NET
Dans les applications ASP.NET qui utilisent [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , vous utilisez le <xref:System.Web.UI.WebControls.LinqDataSource> contrôle serveur Web. Le contrôle gère la plus grande partie de la logique qu’il doit avoir pour interroger [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , passer les données au navigateur, les récupérer et les soumettre à [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> qui met ensuite à jour la base de données. Vous configurez simplement le contrôle dans le balisage et le contrôle gère tous les transferts de données entre [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] et le navigateur. Étant donné que le contrôle gère les interactions avec la couche présentation et [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] gère la communication avec la couche données, votre principal objectif dans les applications multicouches ASP.net est l’écriture de votre logique métier personnalisée.  
  
 Pour plus d’informations sur `LINQDataSource` , consultez [vue d’ensemble du contrôle serveur Web LinqDataSource](/previous-versions/aspnet/bb547113(v=vs.100)).  
  
## <a name="see-also"></a>Voir aussi

- [Applications multicouches et distantes avec LINQ to SQL](n-tier-and-remote-applications-with-linq-to-sql.md)
