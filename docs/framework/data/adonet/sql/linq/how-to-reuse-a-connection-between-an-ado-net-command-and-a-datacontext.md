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
# <a name="how-to-reuse-a-connection-between-an-adonet-command-and-a-datacontext"></a>Procédure : Réutiliser une connexion entre une commande ADO.NET et un DataContext
Étant [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] donné que fait partie de la famille de technologies ADO.net et est basé sur les services fournis par ADO.net, vous pouvez réutiliser une connexion entre une commande <xref:System.Data.Linq.DataContext>ADO.net et un.  
  
## <a name="example"></a>Exemples  
 L’exemple suivant montre comment réutiliser la même connexion entre une commande ADO.NET et le <xref:System.Data.Linq.DataContext>.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>Voir aussi

- [Informations générales](background-information.md)
- [ADO.NET et LINQ to SQL](ado-net-and-linq-to-sql.md)
- [Communication avec la base de données](communicating-with-the-database.md)
