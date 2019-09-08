---
title: Formuler des projections
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 745742df-0eda-479b-83f8-29bd8a80db96
ms.openlocfilehash: 0dfd5d951750de2ab918c51dd9f4f2deeb8a6318
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793818"
---
# <a name="formulate-projections"></a>Formuler des projections
Les exemples suivants montrent comment l' `select` instruction dans C# et `Select` l’instruction dans Visual Basic peuvent être combinées avec d’autres fonctionnalités pour former des projections de requête.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise la `Select` clause dans Visual Basic (`select` clause dans C#) pour retourner une séquence de noms de contact `Customers`pour.  
  
 [!code-csharp[DLinqQueryExamples#57](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#57)]
 [!code-vb[DLinqQueryExamples#57](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#57)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise la `Select` clause dans Visual Basic (`select` clause dans C#) et des *types anonymes* pour retourner une séquence de noms de contact et `Customers`de numéros de téléphone pour.  
  
 [!code-csharp[DLinqQueryExamples#58](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#58)]
 [!code-vb[DLinqQueryExamples#58](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#58)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise la `Select` clause dans Visual Basic (`select` clause dans C#) et des *types anonymes* pour retourner une séquence de noms et de numéros de téléphone pour les employés. Les `FirstName` champs `LastName` et sont combinés en un champ unique (`Name`) `Phone` et le `HomePhone` champ est renommé dans la séquence résultante.  
  
 [!code-csharp[DLinqQueryExamples#59](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#59)]
 [!code-vb[DLinqQueryExamples#59](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#59)]  
  
## <a name="example"></a>Exemples  
 L’exemple suivant utilise la `Select` clause dans Visual Basic (`select` clause dans C#) et des *types anonymes* pour retourner une séquence `ProductID`de tous les et une valeur `HalfPrice`calculée nommée. Cette valeur correspond à `UnitPrice` divisé par 2.  
  
 [!code-csharp[DLinqQueryExamples#60](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#60)]
 [!code-vb[DLinqQueryExamples#60](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#60)]  
  
## <a name="example"></a>Exemples  
 L’exemple suivant utilise la `Select` clause dans Visual Basic (`select` clause dans C#) et une *instruction conditionnelle* pour retourner une séquence de nom de produit et de disponibilité du produit.  
  
 [!code-csharp[DLinqQueryExamples#61](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#61)]
 [!code-vb[DLinqQueryExamples#61](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#61)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise une clause `Select` Visual Basic (`select` clause dans C#) et un *type connu* (nom) pour retourner une séquence des noms des employés.  
  
 [!code-csharp[DLinqQueryExamples#62](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#62)]
 [!code-vb[DLinqQueryExamples#62](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#62)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise `Select` et `Where` dans Visual Basic (`select` et `where` dans C#) pour retourner une *séquence filtrée* de noms de contact pour les clients de Londres.  
  
 [!code-csharp[DLinqQueryExamples#63](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#63)]
 [!code-vb[DLinqQueryExamples#63](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#63)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise une `Select` clause dans Visual Basic (`select` clause dans C#) et des *types anonymes* pour retourner un *sous-ensemble mis en forme* des données relatives aux clients.  
  
 [!code-csharp[DLinqQueryExamples#64](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#64)]
 [!code-vb[DLinqQueryExamples#64](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#64)]  
  
## <a name="example"></a>Exemples  
 L'exemple suivant utilise des requêtes imbriquées pour retourner les résultats suivants :  
  
- Séquence de toutes les commandes et des `OrderID` correspondants.  
  
- Sous-séquence des éléments dans la commande pour laquelle il existe une remise.  
  
- Montant enregistré si le coût d'expédition n'est pas inclus.  
  
 [!code-csharp[DLinqQueryExamples#65](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#65)]
 [!code-vb[DLinqQueryExamples#65](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#65)]  
  
## <a name="see-also"></a>Voir aussi

- [Exemples de requêtes](query-examples.md)
