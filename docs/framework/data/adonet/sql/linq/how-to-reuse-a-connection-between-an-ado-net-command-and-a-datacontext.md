---
title: 'Procédure : Réutiliser une connexion entre une commande ADO.NET et un DataContext'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e26c7eb-c18a-43b5-a8f0-28fd8b04b0f0
ms.openlocfilehash: f1ee7726042327eae88e69e9e6d062909c5bc74e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793291"
---
# <a name="how-to-reuse-a-connection-between-an-adonet-command-and-a-datacontext"></a><span data-ttu-id="efe44-102">Procédure : Réutiliser une connexion entre une commande ADO.NET et un DataContext</span><span class="sxs-lookup"><span data-stu-id="efe44-102">How to: Reuse a Connection Between an ADO.NET Command and a DataContext</span></span>
<span data-ttu-id="efe44-103">Étant [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] donné que fait partie de la famille de technologies ADO.net et est basé sur les services fournis par ADO.net, vous pouvez réutiliser une connexion entre une commande <xref:System.Data.Linq.DataContext>ADO.net et un.</span><span class="sxs-lookup"><span data-stu-id="efe44-103">Because [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] is a part of the ADO.NET family of technologies and is based on services provided by ADO.NET, you can reuse a connection between an ADO.NET command and a <xref:System.Data.Linq.DataContext>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="efe44-104">Exemples</span><span class="sxs-lookup"><span data-stu-id="efe44-104">Example</span></span>  
 <span data-ttu-id="efe44-105">L’exemple suivant montre comment réutiliser la même connexion entre une commande ADO.NET et le <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="efe44-105">The following example shows how to reuse the same connection between an ADO.NET command and the <xref:System.Data.Linq.DataContext>.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="efe44-106">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="efe44-106">See also</span></span>

- [<span data-ttu-id="efe44-107">Informations générales</span><span class="sxs-lookup"><span data-stu-id="efe44-107">Background Information</span></span>](background-information.md)
- [<span data-ttu-id="efe44-108">ADO.NET et LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="efe44-108">ADO.NET and LINQ to SQL</span></span>](ado-net-and-linq-to-sql.md)
- [<span data-ttu-id="efe44-109">Communication avec la base de données</span><span class="sxs-lookup"><span data-stu-id="efe44-109">Communicating with the Database</span></span>](communicating-with-the-database.md)
