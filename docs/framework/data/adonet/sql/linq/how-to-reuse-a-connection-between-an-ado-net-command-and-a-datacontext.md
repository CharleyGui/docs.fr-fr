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
# <a name="how-to-reuse-a-connection-between-an-adonet-command-and-a-datacontext"></a>Procédure : Réutiliser une connexion entre une commande ADO.NET et un DataContext

Étant donné que [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] fait partie de la famille de technologies ADO.net et est basé sur les services fournis par ADO.net, vous pouvez réutiliser une connexion entre une commande ADO.net et un <xref:System.Data.Linq.DataContext> .  
  
## <a name="example"></a>Exemple  

 L’exemple suivant montre comment réutiliser la même connexion entre une commande ADO.NET et le <xref:System.Data.Linq.DataContext> .  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>Voir aussi

- [Informations générales](background-information.md)
- [ADO.NET et LINQ to SQL](ado-net-and-linq-to-sql.md)
- [Communication avec la base de données](communicating-with-the-database.md)
