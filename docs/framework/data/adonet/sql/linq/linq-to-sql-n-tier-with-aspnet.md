---
title: Applications multicouches LINQ to SQL avec ASP.NET
ms.date: 03/30/2017
ms.assetid: f6cc863a-d6a6-4281-ba8b-197c01cf6c6f
ms.openlocfilehash: a184c9dcb29e7994aefa4062be2b30484539c4e1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175315"
---
# <a name="linq-to-sql-n-tier-with-aspnet"></a><span data-ttu-id="873b2-102">Applications multicouches LINQ to SQL avec ASP.NET</span><span class="sxs-lookup"><span data-stu-id="873b2-102">LINQ to SQL N-Tier with ASP.NET</span></span>

<span data-ttu-id="873b2-103">Dans les applications ASP.NET qui utilisent [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , vous utilisez le <xref:System.Web.UI.WebControls.LinqDataSource> contrôle serveur Web.</span><span class="sxs-lookup"><span data-stu-id="873b2-103">In ASP.NET applications that use [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you use the <xref:System.Web.UI.WebControls.LinqDataSource> Web server control.</span></span> <span data-ttu-id="873b2-104">Le contrôle gère la plus grande partie de la logique qu’il doit avoir pour interroger [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , passer les données au navigateur, les récupérer et les soumettre à [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> qui met ensuite à jour la base de données.</span><span class="sxs-lookup"><span data-stu-id="873b2-104">The control handles most of the logic that it must have to query against [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], pass the data to the browser, retrieve it, and submit it to the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> which then updates the database.</span></span> <span data-ttu-id="873b2-105">Vous configurez simplement le contrôle dans le balisage et le contrôle gère tous les transferts de données entre [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] et le navigateur.</span><span class="sxs-lookup"><span data-stu-id="873b2-105">You just configure the control in the markup, and the control handles all the data transfer between [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] and the browser.</span></span> <span data-ttu-id="873b2-106">Étant donné que le contrôle gère les interactions avec la couche présentation et [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] gère la communication avec la couche données, votre principal objectif dans les applications multicouches ASP.net est l’écriture de votre logique métier personnalisée.</span><span class="sxs-lookup"><span data-stu-id="873b2-106">Because the control handles the interactions with the presentation tier, and [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] handles the communication with the data tier, your main focus in ASP.NET multitier applications is on writing your custom business logic.</span></span>  
  
 <span data-ttu-id="873b2-107">Pour plus d’informations sur `LINQDataSource` , consultez [vue d’ensemble du contrôle serveur Web LinqDataSource](/previous-versions/aspnet/bb547113(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="873b2-107">For more information about `LINQDataSource`, see [LinqDataSource Web Server Control Overview](/previous-versions/aspnet/bb547113(v=vs.100)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="873b2-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="873b2-108">See also</span></span>

- [<span data-ttu-id="873b2-109">Applications multicouches et distantes avec LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="873b2-109">N-Tier and Remote Applications with LINQ to SQL</span></span>](n-tier-and-remote-applications-with-linq-to-sql.md)
