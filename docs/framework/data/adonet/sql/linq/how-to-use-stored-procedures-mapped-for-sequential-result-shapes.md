---
title: 'Procédure : Utiliser des procédures stockées mappées pour des formes de résultats séquentielles'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a73530de-5a4e-4d9c-8d66-abb19c225b11
ms.openlocfilehash: 8378a175ab2479ab9769ca08579e1c89269eaba4
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003221"
---
# <a name="how-to-use-stored-procedures-mapped-for-sequential-result-shapes"></a>Procédure : Utiliser des procédures stockées mappées pour des formes de résultats séquentielles
Ce type de procédure stockée peut générer plusieurs formes de résultats, mais vous savez dans quel ordre les résultats sont retournés. Comparez ce scénario à celui dans lequel vous ne connaissez pas la séquence des retours. Pour plus d'informations, voir [Procédure : Utilisez des procédures stockées mappées pour plusieurs formes de résultats @ no__t-0.  
  
## <a name="example"></a>Exemple  
 Le T-SQL d'une procédure stockée qui retourne plusieurs formes de résultats de manière séquentielle est présenté ci-dessous :  
  
```sql
CREATE PROCEDURE MultipleResultTypesSequentially  
AS  
select * from products  
select * from customers  
```  
  
 [!code-csharp[DLinqSprox#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#6)]
 [!code-vb[DLinqSprox#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#6)]  
  
## <a name="example"></a>Exemple  
 Vous pouvez utiliser un code semblable à celui qui suit pour exécuter cette procédure stockée.  
  
 [!code-csharp[DLinqSprox#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#7)]
 [!code-vb[DLinqSprox#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#7)]  
  
## <a name="see-also"></a>Voir aussi

- [Procédures stockées](stored-procedures.md)
