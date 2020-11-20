---
title: Gestion des valeurs null
description: En savoir plus sur la façon dont le Fournisseur de données .NET Framework pour SQL Server gère la valeur null, et en savoir plus sur la valeur null et SqlBoolean, la logique à trois valeurs et l’assignation de valeurs NULL.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f18b288f-b265-4bbe-957f-c6833c0645ef
ms.openlocfilehash: 2dda65f605ea9de616f01d6e52eb4e0e5def4db7
ms.sourcegitcommit: 6d1ae17e60384f3b5953ca7b45ac859ec6d4c3a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2020
ms.locfileid: "94982516"
---
# <a name="handling-null-values"></a>Gestion des valeurs null

Une valeur Null dans une base de données relationnelle est utilisée lorsque la valeur d’une colonne est inconnue ou manquante. Une valeur Null n’est ni une chaîne vide (pour les types de données caractère ou DateHeure), ni une valeur zéro (pour les types de données numériques). La spécification SQL-92 ANSI indique qu’une valeur Null doit être la même pour tous les types de données, de sorte que toutes les valeurs Null sont gérées de manière cohérente. L’espace de noms <xref:System.Data.SqlTypes> fournit une sémantique Null en implémentant l’interface <xref:System.Data.SqlTypes.INullable>. Chacun des types de données de <xref:System.Data.SqlTypes> a sa propre propriété `IsNull` et une valeur `Null` qui peut être assignée à une instance de ce type de données.  
  
> [!NOTE]
> La version 2,0 de .NET Framework a introduit la prise en charge des types valeur Nullable, qui permettent aux programmeurs d’étendre un type valeur pour représenter toutes les valeurs du type sous-jacent. Ces types valeur CLR Nullable représentent une instance de la <xref:System.Nullable> structure. Cette fonctionnalité est particulièrement utile lorsque les types valeur sont boxed et unboxed, ce qui offre une meilleure compatibilité avec les types d’objets. Les types valeur CLR Nullable ne sont pas destinés au stockage des valeurs null de base de données, car une valeur null SQL ANSI ne se comporte pas de la même façon qu’une `null` référence (ou `Nothing` dans Visual Basic). Pour travailler avec les valeurs Null SQL ANSI de la base de données, utilisez les valeurs Null <xref:System.Data.SqlTypes> au lieu de <xref:System.Nullable>. Pour plus d’informations sur l’utilisation des types Nullable de valeur CLR dans Visual Basic consultez [types valeur Nullable](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md), et pour C#, consultez [types valeur Nullable](../../../../csharp/language-reference/builtin-types/nullable-value-types.md).  
  
## <a name="nulls-and-three-valued-logic"></a>Valeurs null et logique à trois valeurs  

 L’autorisation de valeurs Null dans les définitions de colonne introduit une logique ternaire dans votre application. Une comparaison peut évaluer entre une et trois conditions :  
  
- True  
  
- False  
  
- Unknown  
  
 Étant donné que la valeur Null est considérée comme inconnue, deux valeurs Null comparées l’une avec l’autre ne sont pas considérées comme égales. Dans les expressions utilisant des opérateurs arithmétiques, si l’un des opérandes a la valeur Null, le résultat est également Null.  
  
## <a name="nulls-and-sqlboolean"></a>Valeurs Null et SqlBoolean  

 La comparaison entre tout <xref:System.Data.SqlTypes> retourne une <xref:System.Data.SqlTypes.SqlBoolean>. La fonction `IsNull` pour chaque `SqlType` retourne un <xref:System.Data.SqlTypes.SqlBoolean> et peut être utilisée pour vérifier les valeurs Null. Les tables de vérité suivantes montrent comment les opérateurs AND, OR et NOT fonctionnent dans la présence d’une valeur Null. (T = true (vrai), F = false (faux) et U = unknown (inconnu) ou Null.)  
  
 ![Table de vérité](./media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")  
  
### <a name="understanding-the-ansi_nulls-option"></a>Compréhension de l'option ANSI_NULLS  

 <xref:System.Data.SqlTypes> fournit la même sémantique que lorsque l’option ANSI_NULLS est activée dans SQL Server. Tous les opérateurs arithmétiques (+,-, \* ,/,%), les opérateurs de bits (~, &, \| ) et la plupart des fonctions retournent Null si l’un des opérandes ou arguments a la valeur null, à l’exception de la propriété `IsNull` .  
  
 La norme ANSI SQL-92 ne prend pas en charge *columnName* = NULL dans une clause WHERE. Dans SQL Server, l’option ANSI_NULLS contrôle à la fois la possibilité de valeur Null par défaut dans la base de données et l’évaluation des comparaisons par rapport aux valeurs Null. Si ANSI_NULLS est activé (valeur par défaut), l’opérateur IS NULL doit être utilisé dans les expressions lors du test des valeurs Null. Par exemple, la comparaison suivante donne toujours un résultat inconnu quand ANSI_NULLS est activé :  
  
```sql
colname > NULL  
```  
  
 La comparaison avec une variable contenant une valeur Null génère également Inconnu :  
  
```sql
colname > @MyVariable  
```  
  
 Utilisez le prédicat IS NULL ou IS NOT NULL pour tester si une valeur est NULL. Ceci peut compliquer encore la clause WHERE. Par exemple, la colonne TerritoryID de la table AdventureWorks Customer autorise les valeurs Null. Si une instruction SELECT doit rechercher des valeurs NULL en plus des autres, elle doit inclure un prédicat IS NULL :  
  
```sql
SELECT CustomerID, AccountNumber, TerritoryID  
FROM AdventureWorks.Sales.Customer  
WHERE TerritoryID IN (1, 2, 3)  
   OR TerritoryID IS NULL  
```  
  
 Si vous désactivez ANSI_NULLS dans SQL Server, vous pouvez créer des expressions qui utilisent l’opérateur d’égalité pour effectuer une comparaison avec la valeur Null. Toutefois, vous ne pouvez pas empêcher des connexions différentes de définir des options Null pour cette connexion. L’utilisation de IS NULL pour tester les valeurs Null fonctionne toujours, quels que soient les paramètres de ANSI_NULLS pour une connexion.  
  
 La désactivation de ANSI_NULLS n’est pas prise en charge dans un `DataSet`, qui suit toujours la norme ANSI SQL-92 pour la gestion des valeurs Null dans <xref:System.Data.SqlTypes>.  
  
## <a name="assigning-null-values"></a>Assignation de valeurs null  

 Les valeurs Null sont spéciales et leur sémantique de stockage et d’affectation diffère selon les systèmes de stockage et systèmes de type. Un `Dataset` est conçu pour être utilisé avec différents systèmes de type et de stockage.  
  
 Cette section décrit la sémantique Null pour l’affectation de valeurs Null à un <xref:System.Data.DataColumn> dans un <xref:System.Data.DataRow> sur les différents systèmes de type.  
  
 `DBNull.Value`  
 Cette affectation est valide pour un `DataColumn` de n’importe quel type. Si le type implémente `INullable`, `DBNull.Value` est forcé dans la valeur Null fortement typée appropriée.  
  
 `SqlType.Null`  
 Tous les types de données <xref:System.Data.SqlTypes> implémentent `INullable`. Si la valeur Null fortement typée peut être convertie dans le type de données de la colonne à l’aide d’opérateurs de forçage de type implicite, l’affectation doit y être soumise. Sinon, une exception de forçage de type non valide est levée.  
  
 `null`  
 Si « Null » est une valeur autorisée pour le type de données `DataColumn` donné, il est converti en `DbNull.Value` approprié ou `Null` associé au type de `INullable` (`SqlType.Null`)  
  
 `derivedUdt.Null`  
 Pour les colonnes UDT, les valeurs Null sont toujours stockées en fonction du type associé à `DataColumn`. Prenons le cas d’un UDT associé à un `DataColumn` qui n’implémente pas `INullable` alors que sa sous-classe le fait. Dans ce cas, si une valeur Null fortement typée associée à la classe dérivée est attribuée, elle est stockée en tant que `DbNull.Value` non typée, car le stockage Null est toujours cohérent avec le type de données de DataColumn.  
  
> [!NOTE]
> La structure `Nullable<T>` ou <xref:System.Nullable> n’est pas prise en charge actuellement dans le `DataSet`.  
  
### <a name="multiple-column-row-assignment"></a>Assignation de plusieurs colonnes (lignes)  

 `DataTable.Add`, `DataTable.LoadDataRow` ou d’autres API acceptant une <xref:System.Data.DataRow.ItemArray%2A> mappée à une ligne, mappez « Null » à la valeur par défaut de DataColumn. Si un objet du tableau contient `DbNull.Value` ou son équivalent fortement typé, les mêmes règles que celles décrites ci-dessus sont appliquées.  
  
 En outre, les règles suivantes s’appliquent à une instance des affectations Null `DataRow.["columnName"]` :  
  
1. La valeur *par défaut* est `DbNull.Value` pour toutes les colonnes à l’exception des colonnes null fortement typées où il s’agit de la valeur null fortement typée appropriée.  
  
2. Les valeurs Null ne sont jamais écrites lors de la sérialisation vers des fichiers XML (comme dans « xsi:nil »).  
  
3. Toutes les valeurs non Null, y compris les valeurs par défaut, sont toujours écrites lors de la sérialisation en XML. Contrairement à la sémantique XSD/XML, où une valeur Null (xsi:nil) est explicite et que la valeur par défaut est implicite (si elle n’est pas présente dans XML, un analyseur de validation peut l’obtenir à partir d’un schéma XSD associé). Le contraire est vrai pour une `DataTable` : une valeur Null est implicite et la valeur par défaut est explicite.  
  
4. La Valeur Null est attribuée à toutes les valeurs de colonne manquantes pour les lignes lues à partir de l’entrée XML. La valeur par défaut de DataColumn est attribuée aux lignes créées à l’aide de <xref:System.Data.DataTable.NewRow%2A> ou à des méthodes similaires.  
  
5. La méthode <xref:System.Data.DataRow.IsNull%2A> renvoie `true` pour `DbNull.Value` et `INullable.Null`.  
  
## <a name="assigning-null-values"></a>Assignation de valeurs null  

 La valeur par défaut pour toute instance <xref:System.Data.SqlTypes> est Null.  
  
 Les valeurs Null dans <xref:System.Data.SqlTypes> sont spécifiques au type et ne peuvent pas être représentées par une valeur unique, telle que `DbNull`. Utilisez la propriété `IsNull` pour vérifier les valeurs Null.  
  
 Les valeurs Null peuvent être attribuées à un <xref:System.Data.DataColumn> comme indiqué dans l’exemple de code suivant. Vous pouvez attribuer directement des valeurs Null à des variables `SqlTypes` sans déclencher d’exception.  
  
### <a name="example"></a>Exemple  

 L’exemple de code suivant crée une <xref:System.Data.DataTable> avec deux colonnes définies comme <xref:System.Data.SqlTypes.SqlInt32> et <xref:System.Data.SqlTypes.SqlString>. Le code ajoute une ligne de valeurs connues, une ligne de valeurs Null, puis itère au sein de la <xref:System.Data.DataTable>, en attribuant les valeurs aux variables et en affichant le résultat dans la fenêtre de console.  
  
 [!code-csharp[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/VB/source.vb#1)]  
  
 Cet exemple produit les résultats suivants :  
  
```output
isColumnNull=False, ID=123, Description=Side Mirror  
isColumnNull=True, ID=Null, Description=Null  
```  
  
## <a name="comparing-null-values-with-sqltypes-and-clr-types"></a>Comparaison de valeurs null à SqlTypes et des types CLR  

 Lors de la comparaison de valeurs Null, il est important de comprendre la différence entre la façon dont la méthode `Equals` évalue les valeurs Null dans les <xref:System.Data.SqlTypes> par rapport à la façon dont elle fonctionne avec les types CLR. Toutes les méthodes <xref:System.Data.SqlTypes>`Equals` utilisent la sémantique de base de données pour évaluer les valeurs Null : si une des valeurs ou les deux sont Null, la comparaison génère la valeur Null. En revanche, l’utilisation de la méthode `Equals` CLR sur deux <xref:System.Data.SqlTypes> produira la valeur true si les deux sont Null. Cela reflète la différence entre l’utilisation d’une méthode d’instance telle que la méthode `String.Equals` CLR et l’utilisation de la méthode statique/partagée, `SqlString.Equals`.  
  
 L’exemple suivant illustre la différence de résultats entre la méthode `SqlString.Equals` et la méthode `String.Equals` quand chacun reçoit une paire de valeurs Null, puis une paire de chaînes vides.  
  
 [!code-csharp[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/VB/source.vb#1)]  
  
 Ce code produit la sortie suivante :  
  
```output
SqlString.Equals shared/static method:  
  Two nulls=Null  
  
String.Equals instance method:  
  Two nulls=True  
  
SqlString.Equals shared/static method:  
  Two empty strings=True  
  
String.Equals instance method:  
  Two empty strings=True
```  
  
## <a name="see-also"></a>Voir aussi

- [Types de données SQL Server et ADO.NET](sql-server-data-types.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
