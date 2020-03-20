---
title: 'Comment : mapper des relations de base de données'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 538def39-8399-46fb-b02d-60ede4e050af
ms.openlocfilehash: c89fb3e11ae8e0f8ea37727446cdf65db9499a1d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148372"
---
# <a name="how-to-map-database-relationships"></a>Comment : mapper des relations de base de données
Vous pouvez encoder comme références de propriété dans votre classe d'entité toutes les relations de données qui seront toujours fixes. Dans l'exemple de base de données Northwind, par exemple, comme les clients passent généralement des commandes, il existe toujours une relation dans le modèle entre les clients et leurs commandes.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]définit un <xref:System.Data.Linq.Mapping.AssociationAttribute> attribut pour aider à représenter de telles relations. Cet attribut est utilisé avec les types <xref:System.Data.Linq.EntitySet%601> et <xref:System.Data.Linq.EntityRef%601> pour représenter ce qui serait une relation de clé étrangère dans une base de données. Pour plus d’informations, consultez la section Attribut de l’Association de [la cartographie basée sur l’attribut](attribute-based-mapping.md).  
  
> [!NOTE]
> Les valeurs des propriétés AssociationAttribute et ColumnAttribute Storage respectent la casse. Assurez-vous, par exemple que les valeurs utilisées dans l'attribut de la propriété AssociationAttribute.Storage correspondent à la casse des noms de propriétés correspondants utilisés ailleurs dans le code. Cela s’applique à tous les langages de programmation .NET, même ceux qui ne sont généralement pas sensibles aux cas, y compris Visual Basic. Pour plus d'informations sur la propriété Storage, consultez <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType>.  
  
 La plupart des relations sont de type un-à-plusieurs, comme dans l'exemple présenté ultérieurement dans cette rubrique. Vous pouvez également représenter les relations de type un-à-un et plusieurs à plusieurs comme suit :  
  
- Relation un-à-un : représentez ce type de relation en incluant <xref:System.Data.Linq.EntitySet%601> des deux côtés.  
  
     Par exemple, `Customer` - `SecurityCode` considérez une relation, créée de sorte que le `Customer` code de sécurité du client ne se trouve pas dans la table et ne peut être consulté que par des personnes autorisées.  
  
- De nombreux : Dans de nombreuses relations, la clé principale de la table de liaison (également appelée la table de *jonction)* est souvent formée par un composite des clés étrangères des deux autres tables.  
  
     Par exemple, `Employee` - `Project` considérez une relation de plusieurs `EmployeeProject`à plusieurs formées en utilisant la table de lien . [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] exige qu'une telle relation soit modélisée à l'aide de trois classes : `Employee`, `Project` et `EmployeeProject`. Dans ce cas, la modification de la relation entre `Employee` et `Project` peut sembler nécessiter une mise à jour de la clé primaire `EmployeeProject`. Toutefois, la modélisation recommandée dans ce cas consiste à supprimer le `EmployeeProject` existant et à créer un autre `EmployeeProject`.  
  
    > [!NOTE]
    > Les relations dans les bases de données relationnelles sont généralement modélisées comme des valeurs de clé étrangère qui font référence aux clés primaires d'autres tables. Pour naviguer entre eux, vous associez explicitement les deux tables en utilisant une opération *de jointure* relationnelle.  
    >
    >  Les [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]objets en, d’autre part, se réfèrent les uns aux autres en utilisant des références de propriété ou des collections de références que vous naviguez en utilisant la notation *point.*  
  
## <a name="example"></a> Exemple  
 Dans l'exemple un-à-plusieurs suivant, la classe `Customer` a une propriété qui déclare la relation entre les clients et leurs commandes.  La propriété `Orders` est de type <xref:System.Data.Linq.EntitySet%601>. Ce type signifie que cette relation est de type un-à-plusieurs (un client et plusieurs commandes). La propriété <xref:System.Data.Linq.Mapping.AssociationAttribute.OtherKey%2A> est utilisée pour décrire comment cette association est accomplie, à savoir, en spécifiant le nom de la propriété dans la classe connexe à comparer avec celle-ci. Dans cet exemple, la `CustomerID` propriété est comparée, tout comme une *joint* de base de données comparerait cette valeur de colonne.  
  
> [!NOTE]
> Si vous utilisez Visual Studio, vous pouvez utiliser le concepteur relationnel d’objet pour créer une association entre les classes.  
  
 [!code-csharp[DlinqCustomize#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#3)]
 [!code-vb[DlinqCustomize#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#3)]  
  
## <a name="example"></a> Exemple  
 Vous pouvez également inverser la situation. Au lieu d'utiliser la classe `Customer` pour décrire l'association entre les clients et les commandes, vous pouvez utiliser la classe `Order`. La classe `Order` utilise le type <xref:System.Data.Linq.EntityRef%601> pour décrire la relation au client, comme dans l'exemple de code suivant.  
  
> [!NOTE]
> La <xref:System.Data.Linq.EntityRef%601> classe prend en charge *le chargement différé*. Pour plus d’informations, *voir* [Deferred versus Immediate Loading](deferred-versus-immediate-loading.md).  
  
 [!code-csharp[DLinqCustomize#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#5)]
 [!code-vb[DLinqCustomize#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Voir aussi

- [Guide pratique pour personnaliser des classes d’entité à l’aide de l’éditeur de code](how-to-customize-entity-classes-by-using-the-code-editor.md)
- [Le modèle d’objet LINQ à SQL](the-linq-to-sql-object-model.md)
