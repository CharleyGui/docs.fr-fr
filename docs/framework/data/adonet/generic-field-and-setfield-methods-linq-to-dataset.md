---
title: Méthodes génériques Field et SetField (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1883365f-9d6c-4ccb-9187-df309f47706d
ms.openlocfilehash: 310eb3ccecc3159234ed362ed044be7ad704dde4
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634831"
---
# <a name="generic-field-and-setfield-methods-linq-to-dataset"></a>Méthodes génériques Field et SetField (LINQ to DataSet)
LINQ to DataSet fournit des méthodes d’extension à la classe <xref:System.Data.DataRow> pour accéder aux valeurs de colonne : la méthode <xref:System.Data.DataRowExtensions.Field%2A> et la méthode <xref:System.Data.DataRowExtensions.SetField%2A>. Ces méthodes facilitent l'accès des développeurs aux valeurs de colonne, particulièrement pour les valeurs Null. L' <xref:System.Data.DataSet> utilise <xref:System.DBNull.Value?displayProperty=nameWithType> pour représenter des valeurs NULL, alors que LINQ utilise les types <xref:System.Nullable> et <xref:System.Nullable%601>. L’utilisation de l’accesseur de colonne préexistant dans <xref:System.Data.DataRow> vous oblige à effectuer un cast de l’objet de retour vers le type approprié. Si un champ particulier d’un <xref:System.Data.DataRow> peut être null, vous devez vérifier explicitement la valeur null, car le retour d' <xref:System.DBNull.Value?displayProperty=nameWithType> et le cast implicite de ce type en un autre type lève une <xref:System.InvalidCastException>. Dans l’exemple suivant, si la méthode <xref:System.Data.DataRow.IsNull%2A?displayProperty=nameWithType> n’a pas été utilisée pour vérifier une valeur null, une exception est levée si l’indexeur a retourné <xref:System.DBNull.Value?displayProperty=nameWithType> et a essayé de le convertir en <xref:System.String>.  
  
 [!code-csharp[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#whereisnull)]
 [!code-vb[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#whereisnull)]  
  
 La méthode <xref:System.Data.DataRowExtensions.Field%2A> donne accès aux valeurs de colonne d'un <xref:System.Data.DataRow> et le <xref:System.Data.DataRowExtensions.SetField%2A> définit les valeurs de colonne dans un <xref:System.Data.DataRow>. Les deux méthodes <xref:System.Data.DataRowExtensions.Field%2A> et <xref:System.Data.DataRowExtensions.SetField%2A> gèrent des types Nullable, ce qui fait que vous n'avez pas à vérifier explicitement les valeurs Null comme dans l'exemple précédent. Les deux méthodes sont également des méthodes génériques, ce qui fait que vous n’avez pas à effectuer un cast du type de retour.  
  
 L'exemple suivant utilise la méthode <xref:System.Data.DataRowExtensions.Field%2A>.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where3)]
 [!code-vb[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where3)]  
  
 Notez que le type de données spécifié dans le paramètre générique `T` de la méthode <xref:System.Data.DataRowExtensions.Field%2A> et de la méthode <xref:System.Data.DataRowExtensions.SetField%2A> doit correspondre au type de la valeur sous-jacente, sinon une exception <xref:System.InvalidCastException> est levée. Le nom de la colonne spécifiée doit également correspondre à celui de la colonne dans le <xref:System.Data.DataSet>, sinon une <xref:System.ArgumentException> est levée. Dans les deux cas, l'exception est levée au moment de l'exécution pendant l'énumération des données lorsque la requête est exécutée.  
  
 La méthode <xref:System.Data.DataRowExtensions.SetField%2A> n'effectue aucune conversion de type. Toutefois, cela ne signifie pas qu'une conversion de type ne se produira pas. La méthode <xref:System.Data.DataRowExtensions.SetField%2A> expose le comportement ADO.NET de la classe <xref:System.Data.DataRow>. Une conversion de type peut être effectuée par l’objet <xref:System.Data.DataRow> et la valeur convertie est alors enregistrée dans l’objet <xref:System.Data.DataRow>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Data.DataRowExtensions>
