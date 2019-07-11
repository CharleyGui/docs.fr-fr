---
title: Serialization2
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a15ae411-8dc2-4ca3-84d2-01c9d5f1972a
ms.openlocfilehash: 1ff6f8b58e01c86ae1c1e2e1533b1997ba2eb6b0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742889"
---
# <a name="serialization"></a>Sérialisation
Cette rubrique décrit [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] fonctions de sérialisation. Les paragraphes qui suivent fournissent des informations sur l'ajout de la sérialisation pendant la génération de code au moment du design et le comportement de sérialisation à l'exécution de classes [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 Vous pouvez ajouter du code de sérialisation au moment du design selon l'un des méthodes suivantes :  
  
- Dans le concepteur objet/relationnel, modifiez le **Mode de sérialisation** propriété **Serialization**.  
  
- Sur la ligne de commande SQLMetal, ajoutez le **/serialization** option. Pour plus d’informations, consultez [SqlMetal.exe (outil de génération de code)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="overview"></a>Présentation  
 Le code généré par [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] fournit des fonctions de chargement différé par défaut. Le chargement différé est très utile au niveau intermédiaire pour le chargement transparent de données à la demande. Il pose toutefois problème pour la sérialisation car le sérialiseur déclenche un chargement différé, qu'il soit voulu ou non. En effet, lorsqu'un objet est sérialisé, sa fermeture transitive dans toutes les références à chargement différé en sortie est sérialisée.  
  
 Le [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] fonctionnalité de sérialisation résout ce problème, principalement par le biais de deux mécanismes :  
  
- Un mode <xref:System.Data.Linq.DataContext> pour désactiver le chargement différé (<xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A>). Pour plus d'informations, consultez <xref:System.Data.Linq.DataContext>.  
  
- Un commutateur de génération de code pour générer des attributs <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType> et <xref:System.Runtime.Serialization.DataMemberAttribute?displayProperty=nameWithType> sur les entités générées. Cet aspect, y compris le comportement de chargement différé des classes lors de la sérialisation, est le principal objet de cette rubrique.  
  
### <a name="definitions"></a>Définitions  
  
- *Sérialiseur DataContract*: Sérialiseur par défaut utilisé par le composant de Windows Communication Framework (WCF) du .NET Framework 3.0 ou versions ultérieures.  
  
- *Sérialisation unidirectionnelle*: La version sérialisée d’une classe qui contient uniquement une propriété d’association unidirectionnelle (pour éviter un cycle). Par convention, la propriété sur le côté parent d'une relation de clé primaire-étrangère est marquée pour sérialisation. L'autre côté d'une association bidirectionnelle n'est pas sérialisé.  
  
     La sérialisation unidirectionnelle est le seul type de sérialisation pris en charge par [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
## <a name="code-example"></a>Exemple de code  
 Le code suivant utilise les classes `Customer` et `Order` standard de l'exemple de base de données Northwind et montre comment ces classes sont décorées avec les attributs de sérialisation.  
  
 [!code-csharp[DLinqSerialization#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#1)]
 [!code-vb[DLinqSerialization#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#1)]  
  
 [!code-csharp[DLinqSerialization#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#2)]
 [!code-vb[DLinqSerialization#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#2)]  
  
 [!code-csharp[DLinqSerialization#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#3)]
 [!code-vb[DLinqSerialization#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#3)]  
  
 Pour la classe `Order` de l'exemple suivant, seule la propriété d'association inverse correspondant à la classe `Customer` est montrée, par souci de concision. Elle n'a pas d'attribut <xref:System.Runtime.Serialization.DataMemberAttribute> pour éviter un cycle.  
  
 [!code-csharp[DLinqSerialization#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#4)]
 [!code-vb[DLinqSerialization#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#4)]  
  
 [!code-csharp[DLinqSerialization#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#5)]
 [!code-vb[DLinqSerialization#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#5)]  
  
### <a name="how-to-serialize-the-entities"></a>Comment sérialiser les entités  
 Vous pouvez sérialiser les entités dans les codes présentés dans la section précédente (voir ci-dessous).  
  
 [!code-csharp[DLinqSerialization#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/Program.cs#6)]
 [!code-vb[DLinqSerialization#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/Module1.vb#6)]  
  
### <a name="self-recursive-relationships"></a>Relations auto-récursives  
 Les relations auto-récursives suivent le même modèle. La propriété d'association qui correspond à la clé étrangère n'a pas d'attribut <xref:System.Runtime.Serialization.DataMemberAttribute>, contrairement à la propriété parente.  
  
 Considérez la classe suivante, qui a deux relations auto-récursives : Employee.Manager/Reports et Employee.mentor/mentees.  
  
 [!code-csharp[DLinqSerialization#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#7)]
 [!code-vb[DLinqSerialization#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#7)]  
  
## <a name="see-also"></a>Voir aussi

- [Informations générales](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [SqlMetal.exe (outil de génération de code)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
- [Guide pratique pour Rendre les entités sérialisables](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md)
