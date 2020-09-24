---
title: Ajout d'une logique métier à l'aide de méthodes partielles
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3a73991e-fd4e-4610-93fb-7ced4dc6b7f9
ms.openlocfilehash: 9ad3329c621b8bf8eaa0fd5f986ac7e8cff97d9e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156158"
---
# <a name="adding-business-logic-by-using-partial-methods"></a>Ajout d'une logique métier à l'aide de méthodes partielles

Vous pouvez personnaliser Visual Basic et le code généré par C# dans vos [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projets à l’aide de *méthodes partielles*. Le code généré par [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] définit des signatures comme faisant partie d'une méthode partielle. Si vous souhaitez implémenter la méthode, vous pouvez ajouter votre propre méthode partielle. Si vous n'ajoutez pas votre propre implémentation, le compilateur ignore la signature de méthodes partielles et appelle les méthodes par défaut dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
> [!NOTE]
> Si vous utilisez Visual Studio, vous pouvez utiliser la Concepteur Objet Relationnel pour ajouter la validation et d’autres personnalisations aux classes d’entité.  
  
 Par exemple, le mappage par défaut pour la classe `Customer` dans l'exemple de base de données Northwind inclut la méthode partielle suivante :  
  
 [!code-csharp[DLinqOverrideDefault#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#2)]
 [!code-vb[DLinqOverrideDefault#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#2)]  
  
 Vous pouvez implémenter votre propre méthode en ajoutant du code tel que le suivant à votre propre classe `Customer` partielle :  
  
 [!code-csharp[DLinqOverrideDefault#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/Program.cs#3)]
 [!code-vb[DLinqOverrideDefault#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/Module1.vb#3)]  
  
 Cette approche est généralement utilisée dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pour substituer des méthodes par défaut pour `Insert` , `Update` , `Delete` et pour valider des propriétés pendant des événements de cycle de vie d’objet.  
  
 Pour plus d’informations, consultez [méthodes partielles](../../../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) (Visual Basic) ou [Partial (méthode) (référence c#)](../../../../../csharp/language-reference/keywords/partial-method.md) (c#).  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  

 L'exemple suivant montre d'abord `ExampleClass` tel qu'il pourrait être défini par un outil de génération de code tel que SQLMetal, puis comment vous pouvez implémenter l'une des deux méthodes seulement.  
  
### <a name="code"></a>Code  

 [!code-csharp[DLinqSubmittingChanges#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#4)]
 [!code-vb[DLinqSubmittingChanges#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#4)]  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  

 L'exemple suivant utilise la relation entre les entités `Shipper` et `Order`. Notez parmi les méthodes celles qui sont partielles, `InsertShipper` et `DeleteShipper`. Ces méthodes remplacent les méthodes partielles par défaut fournies par le [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mappage.  
  
### <a name="code"></a>Code  

 [!code-csharp[DLinqOverrideDefault#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#1)]
 [!code-vb[DLinqOverrideDefault#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- [Apport et soumission de modifications de données](making-and-submitting-data-changes.md)
- [Personnalisation des opérations d'insertion, de mise à jour et de suppression](customizing-insert-update-and-delete-operations.md)
