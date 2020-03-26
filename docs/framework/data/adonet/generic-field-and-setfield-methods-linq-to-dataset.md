---
title: Méthodes génériques Field et SetField (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1883365f-9d6c-4ccb-9187-df309f47706d
ms.openlocfilehash: d7ddee775e91c6be6166a091997afd58113cfe6b
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249101"
---
# <a name="generic-field-and-setfield-methods-linq-to-dataset"></a>Méthodes génériques Field et SetField (LINQ to DataSet)
LINQ à DataSet fournit <xref:System.Data.DataRow> des méthodes d’extension <xref:System.Data.DataRowExtensions.Field%2A> à la <xref:System.Data.DataRowExtensions.SetField%2A> classe pour accéder aux valeurs de colonne : la méthode et la méthode. Ces méthodes facilitent l'accès des développeurs aux valeurs de colonne, particulièrement pour les valeurs Null. Les <xref:System.Data.DataSet> <xref:System.DBNull.Value?displayProperty=nameWithType> utilisations pour représenter des valeurs <xref:System.Nullable> <xref:System.Nullable%601> nulles, tandis que LINQ utilise les et les types. L’utilisation de l’accesseur de colonne <xref:System.Data.DataRow> préexistante vous oblige à lancer l’objet de retour au type approprié. Si un champ <xref:System.Data.DataRow> particulier dans un peut être nul, vous <xref:System.DBNull.Value?displayProperty=nameWithType> devez explicitement vérifier une valeur <xref:System.InvalidCastException>nulle parce que le retour et implicitement le jeter à un autre type jette un . Dans l’exemple suivant, si la <xref:System.Data.DataRow.IsNull%2A?displayProperty=nameWithType> méthode n’était pas utilisée pour vérifier une <xref:System.DBNull.Value?displayProperty=nameWithType> valeur nulle, une <xref:System.String>exception serait jetée si l’indexeur revenait et essayait de la jeter à un .  
  
 [!code-csharp[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#whereisnull)]
 [!code-vb[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#whereisnull)]  
  
 La méthode <xref:System.Data.DataRowExtensions.Field%2A> donne accès aux valeurs de colonne d'un <xref:System.Data.DataRow> et le <xref:System.Data.DataRowExtensions.SetField%2A> définit les valeurs de colonne dans un <xref:System.Data.DataRow>. La <xref:System.Data.DataRowExtensions.Field%2A> méthode <xref:System.Data.DataRowExtensions.SetField%2A> et la méthode traitent les types de valeur nul, de sorte que vous n’avez pas à vérifier explicitement les valeurs nulles comme dans l’exemple précédent. Les deux méthodes sont également des méthodes génériques, ce qui fait que vous n’avez pas à effectuer un cast du type de retour.  
  
 L'exemple suivant utilise la méthode <xref:System.Data.DataRowExtensions.Field%2A>.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where3)]
 [!code-vb[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where3)]  
  
 Notez que le type de données spécifié dans le paramètre générique `T` de la méthode <xref:System.Data.DataRowExtensions.Field%2A> et de la méthode <xref:System.Data.DataRowExtensions.SetField%2A> doit correspondre au type de la valeur sous-jacente, sinon une exception <xref:System.InvalidCastException> est levée. Le nom de la colonne spécifiée doit également correspondre à celui de la colonne dans le <xref:System.Data.DataSet>, sinon une <xref:System.ArgumentException> est levée. Dans les deux cas, l'exception est levée au moment de l'exécution pendant l'énumération des données lorsque la requête est exécutée.  
  
 La méthode <xref:System.Data.DataRowExtensions.SetField%2A> n'effectue aucune conversion de type. Toutefois, cela ne signifie pas qu'une conversion de type ne se produira pas. La <xref:System.Data.DataRowExtensions.SetField%2A> méthode expose le comportement ADO.NET <xref:System.Data.DataRow> de la classe. Une conversion de type <xref:System.Data.DataRow> peut être effectuée par l’objet <xref:System.Data.DataRow> et la valeur convertie serait alors enregistrée à l’objet.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Data.DataRowExtensions>
