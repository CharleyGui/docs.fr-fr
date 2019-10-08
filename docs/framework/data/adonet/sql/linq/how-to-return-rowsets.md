---
title: 'Procédure : Retourner des ensembles de lignes'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 725718f5-da29-4841-9f53-aafef64ba977
ms.openlocfilehash: b853a6f2175009cbcbc01c14a6732b98e37e1a7f
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003060"
---
# <a name="how-to-return-rowsets"></a>Procédure : Retourner des ensembles de lignes
Cet exemple retourne un jeu de lignes de la base de données et inclut un paramètre d'entrée pour filtrer le résultat.  
  
 Quand vous exécutez une procédure stockée qui retourne un ensemble de lignes, vous utilisez une classe de *résultats* qui stocke les retours de la procédure stockée. Pour plus d’informations, consultez [analyse du code source de LINQ to SQL](analyzing-linq-to-sql-source-code.md).  
  
## <a name="example"></a>Exemple  
 L'exemple suivant représente une procédure stockée qui retourne des lignes de clients et utilise un paramètre d'entrée pour retourner uniquement les lignes dont la ville du client est « London ». L'exemple suppose l'existence d'une classe `CustomersByCityResult` dénombrable.  
  
```sql  
CREATE PROCEDURE [dbo].[Customers By City]  
    (@param1 NVARCHAR(20))  
AS  
BEGIN  
    -- SET NOCOUNT ON added to prevent extra result sets from  
    -- interfering with SELECT statements.  
    SET NOCOUNT ON;  
    SELECT CustomerID, ContactName, CompanyName, City from Customers  
        as c where c.City=@param1  
END  
```  
  
 [!code-csharp[DLinqSprox#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#1)]
 [!code-vb[DLinqSprox#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- [Procédures stockées](stored-procedures.md)
- [Téléchargement d’exemples de base de données](downloading-sample-databases.md)
