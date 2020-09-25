---
title: Formuler des projections
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 745742df-0eda-479b-83f8-29bd8a80db96
ms.openlocfilehash: f0bc6dfcff7778ebc7156cbb039e13570c90467b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194399"
---
# <a name="formulate-projections"></a>Formuler des projections

Les exemples suivants montrent comment l' `select` instruction en C# et l' `Select` instruction dans Visual Basic peuvent être combinées avec d’autres fonctionnalités pour former des projections de requête.  
  
## <a name="example"></a>Exemple  

 L’exemple suivant utilise la `Select` clause dans Visual Basic ( `select` clause dans C#) pour retourner une séquence de noms de contact pour `Customers` .  
  
 [!code-csharp[DLinqQueryExamples#57](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#57)]
 [!code-vb[DLinqQueryExamples#57](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#57)]  
  
## <a name="example"></a>Exemple  

 L’exemple suivant utilise la `Select` clause dans Visual Basic ( `select` clause en C#) et des *types anonymes* pour retourner une séquence de noms de contact et de numéros de téléphone pour `Customers` .  
  
 [!code-csharp[DLinqQueryExamples#58](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#58)]
 [!code-vb[DLinqQueryExamples#58](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#58)]  
  
## <a name="example"></a>Exemple  

 L’exemple suivant utilise la `Select` clause dans Visual Basic ( `select` clause en C#) et des *types anonymes* pour retourner une séquence de noms et de numéros de téléphone pour les employés. Les `FirstName` `LastName` champs et sont combinés en un champ unique ( `Name` ) et le `HomePhone` champ est renommé `Phone` dans la séquence résultante.  
  
 [!code-csharp[DLinqQueryExamples#59](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#59)]
 [!code-vb[DLinqQueryExamples#59](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#59)]  
  
## <a name="example"></a>Exemple  

 L’exemple suivant utilise la `Select` clause dans Visual Basic ( `select` clause en C#) et des *types anonymes* pour retourner une séquence de tous les `ProductID` et une valeur calculée nommée `HalfPrice` . Cette valeur correspond à `UnitPrice` divisé par 2.  
  
 [!code-csharp[DLinqQueryExamples#60](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#60)]
 [!code-vb[DLinqQueryExamples#60](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#60)]  
  
## <a name="example"></a>Exemple  

 L’exemple suivant utilise la `Select` clause dans Visual Basic ( `select` clause en C#) et une *instruction conditionnelle* pour retourner une séquence de nom de produit et de disponibilité du produit.  
  
 [!code-csharp[DLinqQueryExamples#61](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#61)]
 [!code-vb[DLinqQueryExamples#61](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#61)]  
  
## <a name="example"></a>Exemple  

 L’exemple suivant utilise une `Select` clause Visual Basic ( `select` clause en C#) et un *type connu* (nom) pour retourner une séquence des noms des employés.  
  
 [!code-csharp[DLinqQueryExamples#62](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#62)]
 [!code-vb[DLinqQueryExamples#62](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#62)]  
  
## <a name="example"></a>Exemple  

 L’exemple suivant utilise `Select` et `Where` dans Visual Basic ( `select` et `where` en C#) pour retourner une *séquence filtrée* de noms de contact pour les clients de Londres.  
  
 [!code-csharp[DLinqQueryExamples#63](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#63)]
 [!code-vb[DLinqQueryExamples#63](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#63)]  
  
## <a name="example"></a>Exemple  

 L’exemple suivant utilise une `Select` clause dans Visual Basic ( `select` clause en C#) et des *types anonymes* pour retourner un *sous-ensemble mis en forme* des données sur les clients.  
  
 [!code-csharp[DLinqQueryExamples#64](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#64)]
 [!code-vb[DLinqQueryExamples#64](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#64)]  
  
## <a name="example"></a>Exemple  

 L'exemple suivant utilise des requêtes imbriquées pour retourner les résultats suivants :  
  
- Séquence de toutes les commandes et des `OrderID` correspondants.  
  
- Sous-séquence des éléments dans la commande pour laquelle il existe une remise.  
  
- Montant enregistré si le coût d'expédition n'est pas inclus.  
  
 [!code-csharp[DLinqQueryExamples#65](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#65)]
 [!code-vb[DLinqQueryExamples#65](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#65)]  
  
## <a name="see-also"></a>Voir aussi

- [Exemples de requêtes](query-examples.md)
