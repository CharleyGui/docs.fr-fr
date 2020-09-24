---
title: 'Procédure : Mapper des relations de base de données'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 538def39-8399-46fb-b02d-60ede4e050af
ms.openlocfilehash: 2f612877f5e7da6442c242aa0d56d811c0aa7cf8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166454"
---
# <a name="how-to-map-database-relationships"></a>Procédure : Mapper des relations de base de données

Vous pouvez encoder comme références de propriété dans votre classe d'entité toutes les relations de données qui seront toujours fixes. Dans l'exemple de base de données Northwind, par exemple, comme les clients passent généralement des commandes, il existe toujours une relation dans le modèle entre les clients et leurs commandes.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] définit un <xref:System.Data.Linq.Mapping.AssociationAttribute> attribut pour aider à représenter de telles relations. Cet attribut est utilisé avec les types <xref:System.Data.Linq.EntitySet%601> et <xref:System.Data.Linq.EntityRef%601> pour représenter ce qui serait une relation de clé étrangère dans une base de données. Pour plus d’informations, consultez la section attribut d’association du [mappage basé sur les attributs](attribute-based-mapping.md).  
  
> [!NOTE]
> Les valeurs des propriétés AssociationAttribute et ColumnAttribute Storage respectent la casse. Assurez-vous, par exemple que les valeurs utilisées dans l'attribut de la propriété AssociationAttribute.Storage correspondent à la casse des noms de propriétés correspondants utilisés ailleurs dans le code. Cela s’applique à tous les langages de programmation .NET, même ceux qui ne sont généralement pas sensibles à la casse, y compris les Visual Basic. Pour plus d'informations sur la propriété Storage, consultez <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType>.  
  
 La plupart des relations sont de type un-à-plusieurs, comme dans l'exemple présenté ultérieurement dans cette rubrique. Vous pouvez également représenter les relations de type un-à-un et plusieurs à plusieurs comme suit :  
  
- Relation un-à-un : représentez ce type de relation en incluant <xref:System.Data.Linq.EntitySet%601> des deux côtés.  
  
     Par exemple, considérez une `Customer` - `SecurityCode` relation créée de sorte que le code de sécurité du client ne soit pas trouvé dans la `Customer` table et qu’il soit accessible uniquement par les personnes autorisées.  
  
- Plusieurs-à-plusieurs : dans les relations plusieurs-à-plusieurs, la clé primaire de la table de liens (également appelée table de *jonction* ) est souvent formée par un composite des clés étrangères des deux autres tables.  
  
     Par exemple, considérez une `Employee` - `Project` relation plusieurs-à-plusieurs formée à l’aide de la table de liens `EmployeeProject` . [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] exige qu'une telle relation soit modélisée à l'aide de trois classes : `Employee`, `Project` et `EmployeeProject`. Dans ce cas, la modification de la relation entre `Employee` et `Project` peut sembler nécessiter une mise à jour de la clé primaire `EmployeeProject`. Toutefois, la modélisation recommandée dans ce cas consiste à supprimer le `EmployeeProject` existant et à créer un autre `EmployeeProject`.  
  
    > [!NOTE]
    > Les relations dans les bases de données relationnelles sont généralement modélisées comme des valeurs de clé étrangère qui font référence aux clés primaires d'autres tables. Pour naviguer entre eux, vous associez explicitement les deux tables à l’aide d’une opération de *jointure* relationnelle.  
    >
    >  En [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] revanche, les objets de font référence les uns aux autres à l’aide de références de propriété ou de collections de références que vous naviguez à l’aide de la notation par *points* .  
  
## <a name="example"></a>Exemple  

 Dans l'exemple un-à-plusieurs suivant, la classe `Customer` a une propriété qui déclare la relation entre les clients et leurs commandes.  La propriété `Orders` est de type <xref:System.Data.Linq.EntitySet%601>. Ce type signifie que cette relation est de type un-à-plusieurs (un client et plusieurs commandes). La propriété <xref:System.Data.Linq.Mapping.AssociationAttribute.OtherKey%2A> est utilisée pour décrire comment cette association est accomplie, à savoir, en spécifiant le nom de la propriété dans la classe connexe à comparer avec celle-ci. Dans cet exemple, la `CustomerID` propriété est comparée, de la même manière qu’une *jointure* de base de données compare cette valeur de colonne.  
  
> [!NOTE]
> Si vous utilisez Visual Studio, vous pouvez utiliser la Concepteur Objet Relationnel pour créer une association entre des classes.  
  
 [!code-csharp[DlinqCustomize#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#3)]
 [!code-vb[DlinqCustomize#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#3)]  
  
## <a name="example"></a>Exemple  

 Vous pouvez également inverser la situation. Au lieu d'utiliser la classe `Customer` pour décrire l'association entre les clients et les commandes, vous pouvez utiliser la classe `Order`. La classe `Order` utilise le type <xref:System.Data.Linq.EntityRef%601> pour décrire la relation au client, comme dans l'exemple de code suivant.  
  
> [!NOTE]
> La <xref:System.Data.Linq.EntityRef%601> classe prend en charge le *chargement différé*. Pour plus d’informations, *consultez* [différé et chargement immédiat](deferred-versus-immediate-loading.md).  
  
 [!code-csharp[DLinqCustomize#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#5)]
 [!code-vb[DLinqCustomize#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Voir aussi

- [Procédure : Personnaliser des classes d’entité à l’aide de l’éditeur de code](how-to-customize-entity-classes-by-using-the-code-editor.md)
- [Modèle objet LINQ to SQL](the-linq-to-sql-object-model.md)
