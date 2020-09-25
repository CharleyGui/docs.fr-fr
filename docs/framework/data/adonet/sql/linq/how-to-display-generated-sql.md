---
title: 'Procédure : Afficher le code SQL généré'
description: Découvrez comment afficher le code SQL généré pour les requêtes à l’aide de la propriété log pour mieux comprendre les fonctionnalités de LINQ to SQL et pour le débogage.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 626492c0-5ee3-4675-88e8-8c40379510b6
ms.openlocfilehash: 81f6b9603cc7f8b7863f787272ce6a1af920fa75
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169490"
---
# <a name="how-to-display-generated-sql"></a><span data-ttu-id="c4288-103">Procédure : Afficher le code SQL généré</span><span class="sxs-lookup"><span data-stu-id="c4288-103">How to: Display Generated SQL</span></span>

<span data-ttu-id="c4288-104">Vous pouvez consulter le code SQL généré pour les requêtes et modifier le traitement à l'aide de la propriété <xref:System.Data.Linq.DataContext.Log%2A>.</span><span class="sxs-lookup"><span data-stu-id="c4288-104">You can view the SQL code generated for queries and change processing by using the <xref:System.Data.Linq.DataContext.Log%2A> property.</span></span> <span data-ttu-id="c4288-105">Cette approche peut être utile pour comprendre les fonctionnalités de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] et déboguer des problèmes spécifiques.</span><span class="sxs-lookup"><span data-stu-id="c4288-105">This approach can be useful for understanding [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] functionality and for debugging specific problems.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4288-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="c4288-106">Example</span></span>  

 <span data-ttu-id="c4288-107">L'exemple suivant utilise la propriété <xref:System.Data.Linq.DataContext.Log%2A> pour afficher le code SQL dans la fenêtre de console avant que son exécution.</span><span class="sxs-lookup"><span data-stu-id="c4288-107">The following example uses the <xref:System.Data.Linq.DataContext.Log%2A> property to display SQL code in the console window before the code is executed.</span></span>  <span data-ttu-id="c4288-108">Vous pouvez utiliser cette propriété avec les commandes de requête, d'insertion, de mise à jour et de suppression.</span><span class="sxs-lookup"><span data-stu-id="c4288-108">You can use this property with query, insert, update, and delete commands.</span></span>  
  
 <span data-ttu-id="c4288-109">Les lignes de la fenêtre de console sont celles que vous voyez lorsque vous exécutez le Visual Basic ou le code C# qui suit.</span><span class="sxs-lookup"><span data-stu-id="c4288-109">The lines from the console window are what you see when you execute the Visual Basic or C# code that follows.</span></span>  
  
```console  
SELECT [t0].[CustomerID], [t0].[CompanyName], [t0].[ContactName], [t0].[ContactT  
itle], [t0].[Address], [t0].[City], [t0].[Region], [t0].[PostalCode], [t0].[Coun  
try], [t0].[Phone], [t0].[Fax]  
FROM [dbo].[Customers] AS [t0]  
WHERE [t0].[City] = @p0  
-- @p0: Input String (Size = 6; Prec = 0; Scale = 0) [London]  
-- Context: SqlProvider(Sql2005) Model: AttributedMetaModel Build: 3.5.20810.0  
```  
  
```console  
AROUT  
BSBEV  
CONSH  
EASTC  
NORTS  
SEVES  
```  
  
 [!code-csharp[DLinqDebuggingSupport#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDebuggingSupport/cs/Program.cs#1)]
 [!code-vb[DLinqDebuggingSupport#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDebuggingSupport/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="c4288-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c4288-110">See also</span></span>

- [<span data-ttu-id="c4288-111">Prise en charge du débogage</span><span class="sxs-lookup"><span data-stu-id="c4288-111">Debugging Support</span></span>](debugging-support.md)
