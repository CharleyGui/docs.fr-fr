---
title: 'Procédure : Afficher le code SQL généré'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 626492c0-5ee3-4675-88e8-8c40379510b6
ms.openlocfilehash: 15fc6a50d232ea12b229b7b2790c0398bc1c370d
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002971"
---
# <a name="how-to-display-generated-sql"></a>Procédure : Afficher le code SQL généré
Vous pouvez consulter le code SQL généré pour les requêtes et modifier le traitement à l'aide de la propriété <xref:System.Data.Linq.DataContext.Log%2A>. Cette approche peut être utile pour comprendre les fonctionnalités de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] et déboguer des problèmes spécifiques.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant utilise la propriété <xref:System.Data.Linq.DataContext.Log%2A> pour afficher le code SQL dans la fenêtre de console avant que son exécution.  Vous pouvez utiliser cette propriété avec les commandes de requête, d'insertion, de mise à jour et de suppression.  
  
 Les lignes de la fenêtre de console sont celles que vous voyez lorsque vous exécutez le C# Visual Basic ou le code qui suit.  
  
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
  
## <a name="see-also"></a>Voir aussi

- [Prise en charge du débogage](debugging-support.md)
