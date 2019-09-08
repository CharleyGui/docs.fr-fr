---
title: 'Procédure : Utiliser des fonctions scalaires définies par l’utilisateur'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 714e252f-c053-4bbb-b1f3-924111cd4d97
ms.openlocfilehash: da4e5e8fe4682191a0c8e2b0ce6a7b945fe63deb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781471"
---
# <a name="how-to-use-scalar-valued-user-defined-functions"></a>Procédure : Utiliser des fonctions scalaires définies par l’utilisateur
Vous pouvez mapper une méthode cliente définie sur une classe à une fonction définie par l'utilisateur à l'aide de l'attribut <xref:System.Data.Linq.Mapping.FunctionAttribute>. Notez que le corps de la méthode construit une expression qui capture l'intention de l'appel de méthode et passe cette expression au <xref:System.Data.Linq.DataContext> pour la traduire et l'exécuter.  
  
> [!NOTE]
> L'exécution directe se produit uniquement si la fonction est appelée à l'extérieur d'une requête. Pour plus d'informations, voir [Procédure : Appelez les fonctions définies par l’utilisateur](how-to-call-user-defined-functions-inline.md)Inline.  
  
## <a name="example"></a>Exemples  
 Le code SQL suivant présente une fonction scalaire `ReverseCustName()` définie par l'utilisateur.  
  
```  
CREATE FUNCTION ReverseCustName(@string varchar(100))  
RETURNS varchar(100)  
AS  
BEGIN  
    DECLARE @custName varchar(100)  
    -- Implementation left as exercise for users.  
    RETURN @custName  
END  
```  
  
 Vous pouvez mapper une méthode cliente telle que la méthode suivante pour ce code :  
  
 [!code-csharp[DLinqUDFS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#3)]
 [!code-vb[DLinqUDFS#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#3)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions définies par l’utilisateur](user-defined-functions.md)
