---
title: 'Procédure : Réutiliser une connexion entre une commande ADO.NET et un DataContext'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e26c7eb-c18a-43b5-a8f0-28fd8b04b0f0
ms.openlocfilehash: 89c9a12399d3d76487d1fdc2bd82aa037c167710
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197350"
---
# <a name="how-to-reuse-a-connection-between-an-adonet-command-and-a-datacontext"></a><span data-ttu-id="89420-102">Procédure : Réutiliser une connexion entre une commande ADO.NET et un DataContext</span><span class="sxs-lookup"><span data-stu-id="89420-102">How to: Reuse a Connection Between an ADO.NET Command and a DataContext</span></span>

<span data-ttu-id="89420-103">Étant donné que [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] fait partie de la famille de technologies ADO.net et est basé sur les services fournis par ADO.net, vous pouvez réutiliser une connexion entre une commande ADO.net et un <xref:System.Data.Linq.DataContext> .</span><span class="sxs-lookup"><span data-stu-id="89420-103">Because [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] is a part of the ADO.NET family of technologies and is based on services provided by ADO.NET, you can reuse a connection between an ADO.NET command and a <xref:System.Data.Linq.DataContext>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89420-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="89420-104">Example</span></span>  

 <span data-ttu-id="89420-105">L’exemple suivant montre comment réutiliser la même connexion entre une commande ADO.NET et le <xref:System.Data.Linq.DataContext> .</span><span class="sxs-lookup"><span data-stu-id="89420-105">The following example shows how to reuse the same connection between an ADO.NET command and the <xref:System.Data.Linq.DataContext>.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="89420-106">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89420-106">See also</span></span>

- [<span data-ttu-id="89420-107">Informations générales</span><span class="sxs-lookup"><span data-stu-id="89420-107">Background Information</span></span>](background-information.md)
- [<span data-ttu-id="89420-108">ADO.NET et LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="89420-108">ADO.NET and LINQ to SQL</span></span>](ado-net-and-linq-to-sql.md)
- [<span data-ttu-id="89420-109">Communication avec la base de données</span><span class="sxs-lookup"><span data-stu-id="89420-109">Communicating with the Database</span></span>](communicating-with-the-database.md)
