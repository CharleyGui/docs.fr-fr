---
title: Gestion des valeurs null
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f18b288f-b265-4bbe-957f-c6833c0645ef
ms.openlocfilehash: 077cfd9b90df130e0a6090637d5dbd70a70930b1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938187"
---
# <a name="handling-null-values"></a>Gestion des valeurs null
Une valeur null dans une base de données relationnelle est utilisée lorsque la valeur d'une colonne est inconnue ou manquante. Une valeur null n'est ni une chaîne vide (pour les types de données caractère ou datetime) ni une valeur zéro (pour les types de données numériques). La spécification ANSI SQL-92 stipule qu'une valeur null doit être la même pour tous les types de données afin que toutes les valeurs null soient traitées de manière cohérente. L'espace de noms <xref:System.Data.SqlTypes> fournit des sémantiques de valeurs null en implémentant l'interface <xref:System.Data.SqlTypes.INullable>. Chacun des types de données de l'espace de noms <xref:System.Data.SqlTypes> possède sa propre propriété `IsNull` et une valeur `Null` qui peut être assignée à une instance de ce type de données.  
  
> [!NOTE]
> L'une des nouveautés de la version 2.0 du .NET Framework est la prise en charge des types Nullable qui permettent aux programmeurs d'étendre un type de valeur pour représenter toutes les valeurs du type sous-jacent. Ces types Nullable CLR représentent une instance de la structure <xref:System.Nullable>. Cette fonctionnalité est tout particulièrement utile lorsque des types de valeurs sont boxed et unboxed, ce qui améliore la compatibilité avec les types d'objets. Les types Nullable CLR ne sont pas destinés au stockage de valeurs de base de données null, car une valeur null SQL ANSI ne se comporte pas de la même manière qu'une référence `null` (ou `Nothing` en Visual Basic). Pour travailler avec des valeurs de base de données null SQL ANSI , utilisez des valeurs null <xref:System.Data.SqlTypes> plutôt que <xref:System.Nullable>. Pour plus d’informations sur l’utilisation des types CLR Nullable dans Visual Basic consultez [types valeur Nullable](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md), C# et pour voir [utilisation de types Nullable](../../../../csharp/programming-guide/nullable-types/using-nullable-types.md).  
  
## <a name="nulls-and-three-valued-logic"></a>Valeurs null et logique à trois valeurs  
 Permettre des valeurs null dans des définitions de colonnes introduit une logique à trois valeurs dans votre application. Une comparaison peut correspondre à l'une des trois conditions :  
  
- True  
  
- False  
  
- Inconnu  
  
 Comme la valeur null est considérée comme inconnue, les deux valeurs null comparées l'une à l'autre ne sont pas considérées comme égales. Dans des expressions utilisant des opérateurs arithmétiques, si l'un des opérandes est une valeur null, le résultat est une valeur null également.  
  
## <a name="nulls-and-sqlboolean"></a>Valeurs null et SqlBoolean  
 La comparaison entre tout <xref:System.Data.SqlTypes> retournera un <xref:System.Data.SqlTypes.SqlBoolean>. La fonction `IsNull` de chaque `SqlType` retourne un <xref:System.Data.SqlTypes.SqlBoolean> et peut être utilisée pour vérifier les valeurs null. Les tables de vérité suivantes montrent comment les opérateurs AND, OR et NOT fonctionnent en présence d'une valeur null (T=true, F=false et U=inconnu ou null).  
  
 ![Table de vérité](../../../../../docs/framework/data/adonet/sql/media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")  
  
### <a name="understanding-the-ansi_nulls-option"></a>Compréhension de l'option ANSI_NULLS  
 <xref:System.Data.SqlTypes> offre les mêmes sémantiques que lorsque l'option ANSI_NULLS est définie dans SQL Server. Tous les opérateurs arithmétiques (+,-, *,/,%), les opérateurs de bits ( &#124;~, &,) et la plupart des fonctions retournent Null si l’un des opérandes ou arguments `IsNull`a la valeur null, à l’exception de la propriété.  
  
 La norme ANSI SQL-92 ne prend pas en charge *ColumnName* = null dans une clause WHERE. Dans SQL Server, l'option ANSI_NULLS contrôle la possibilité de nullité par défaut dans la base de données et l'évaluation des comparaisons par rapport à des valeurs null. Si ANSI_NULLS est activée (par défaut), l'opérateur IS NULL doit être utilisé dans des expressions lors du test des valeurs null. Par exemple, la comparaison suivante entraîne toujours une valeur inconnue si ANSI_NULLS est activée :  
  
```  
colname > NULL  
```  
  
 La comparaison avec une variable contenant une valeur null entraîne également une valeur inconnue :  
  
```  
colname > @MyVariable  
```  
  
 Utilisez le prédicat IS NULL ou IS NOT NULL pour tester une valeur null. Cela peut compliquer la clause WHERE. Par exemple, la colonne TerritoryID de la table AdventureWorks Customer autorise les valeurs null. Si une instruction SELECT doit tester des valeurs null en plus des autres, elle doit inclure un prédicat IS NULL :  
  
```  
SELECT CustomerID, AccountNumber, TerritoryID  
FROM AdventureWorks.Sales.Customer  
WHERE TerritoryID IN (1, 2, 3)  
   OR TerritoryID IS NULL  
```  
  
 Si vous désactivez ANSI_NULLS dans SQL Server, vous pouvez créer des expressions qui utilisent l'opérateur d'égalité pour effectuer une comparaison par rapport à une valeur null. Cependant, vous ne pouvez pas empêcher des connexions différentes de définir des options null pour cette connexion. L'utilisation de IS NULL pour tester des valeurs null fonctionne toujours, indépendamment des paramètres ANSI_NULLS pour une connexion.  
  
 La désactivation de ANSI_NULLS n'est pas prise en charge dans un `DataSet`, qui respecte toujours la norme ANSI SQL-92 relative à la gestion des valeurs null dans <xref:System.Data.SqlTypes>.  
  
## <a name="assigning-null-values"></a>Assignation de valeurs null  
 Les valeurs null sont spéciales et leurs sémantiques de stockage et d'assignation varient selon les systèmes de types et de stockage. Un `Dataset` est conçu pour être utilisé avec différents systèmes de types et de stockage.  
  
 Cette section décrit la sémantique des valeurs null pour l'assignation des valeurs null à un <xref:System.Data.DataColumn> dans un <xref:System.Data.DataRow> dans différents systèmes de types.  
  
 `DBNull.Value`  
 Cette assignation est valide pour un `DataColumn` de n'importe quel type. Si le type implémente `INullable`, `DBNull.Value` est converti dans la valeur null fortement typée appropriée.  
  
 `SqlType.Null`  
 Tous les types de données <xref:System.Data.SqlTypes> implémentent `INullable`. Si la valeur null fortement typée peut être convertie dans le type données de la colonne à l'aide des opérateurs cast implicites, l'assignation doit continuer. Si tel n'est pas le cas, une exception cast non valide est levée.  
  
 `null`  
 Si 'null' est une valeur autorisée pour le type de données `DataColumn`, elle est convertie en `DbNull.Value` ou `Null` approprié en association avec le type `INullable` (`SqlType.Null`)  
  
 `derivedUdt.Null`  
 Pour les colonnes UDT, les valeurs null sont toujours stockées en fonction du type associé à `DataColumn`. Considérons le cas d'un UDT associé à un `DataColumn` qui n'implémente pas `INullable` contrairement à sa sous-classe. Dans ce cas, si une valeur null fortement typée associée à la classe dérivée est assignée, elle est stockée en tant que `DbNull.Value` non typé, car le stockage de valeurs null est toujours cohérent avec le type de données de DataColumn.  
  
> [!NOTE]
> La structure `Nullable<T>` ou <xref:System.Nullable> n'est actuellement pas prise en charge dans le `DataSet`.  
  
### <a name="multiple-column-row-assignment"></a>Assignation de plusieurs colonnes (lignes)  
 `DataTable.Add`, `DataTable.LoadDataRow` ou toute autre API acceptant une propriété <xref:System.Data.DataRow.ItemArray%2A> qui obtient le mappage à une ligne, mappe 'null' à la valeur par défaut de DataColumn. Si un objet du tableau contient `DbNull.Value` ou son équivalent fortement typé, les mêmes règles que celles décrites précédemment s'appliquent.  
  
 Par ailleurs, les règles suivantes s'appliquent à une instance des assignations null `DataRow.["columnName"]` :  
  
1. La valeur par *défaut* est `DbNull.Value` pour toutes les colonnes à l’exception des colonnes null fortement typées où il s’agit de la valeur null fortement typée appropriée.  
  
2. Les valeurs null ne sont jamais écrites durant la sérialisation en fichiers XML (comme dans « xsi:nil »).  
  
3. Toutes les valeurs non null, y compris les valeurs par défaut, sont toujours écrites durant la sérialisation en XML. Cela est contraire à la sémantique XSD/XML où une valeur null (xsi:nil) est explicite et la valeur par défaut est implicite (s'il n'est pas présent dans XML, un analyseur validant peut l'obtenir d'un schéma XSD associé). Le contraire est vrai pour `DataTable` : une valeur null est implicite et la valeur par défaut est explicite.  
  
4. La valeur NULL est assignée à toutes les valeurs de colonne manquantes pour les lignes lues à partir de l'entrée XML. La valeur par défaut de DataColumn est assignée aux lignes créées à l'aide de <xref:System.Data.DataTable.NewRow%2A> ou de méthodes similaires.  
  
5. La méthode <xref:System.Data.DataRow.IsNull%2A> retourne `true` pour  `DbNull.Value` et `INullable.Null`.  
  
## <a name="assigning-null-values"></a>Assignation de valeurs null  
 La valeur par défaut pour toute instance <xref:System.Data.SqlTypes> est null.  
  
 Les valeurs null dans <xref:System.Data.SqlTypes> sont spécifiques aux types et ne peuvent pas être représentées par une simple valeur, telle que `DbNull`. Utilisez la propriété `IsNull` pour vérifier les valeurs null.  
  
 Les valeurs null peuvent être assignées à un <xref:System.Data.DataColumn> comme illustré dans l'exemple de code suivant. Vous pouvez assigner directement des valeurs null à des variables `SqlTypes` sans lever une exception.  
  
### <a name="example"></a>Exemple  
 L'exemple de code suivant crée un <xref:System.Data.DataTable> avec deux colonnes définies comme <xref:System.Data.SqlTypes.SqlInt32> et <xref:System.Data.SqlTypes.SqlString>. Le code ajoute une ligne de valeurs connues, une ligne de valeurs null, puis itère au sein du <xref:System.Data.DataTable>, assignant les valeurs à des variables et affichant la sortie dans la fenêtre de console.  
  
 [!code-csharp[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/VB/source.vb#1)]  
  
 Cet exemple affiche les résultats suivants :  
  
```  
isColumnNull=False, ID=123, Description=Side Mirror  
isColumnNull=True, ID=Null, Description=Null  
```  
  
## <a name="comparing-null-values-with-sqltypes-and-clr-types"></a>Comparaison de valeurs null à SqlTypes et des types CLR  
 Lors de la comparaison de valeurs null, il est important de comprendre la différence entre la manière dont la méthode `Equals` évalue les valeurs null dans <xref:System.Data.SqlTypes> et celle dont elle fonctionne avec les types CLR. Toutes les méthodes <xref:System.Data.SqlTypes>`Equals` utilisent des sémantiques de base de données pour évaluer des valeurs null : si au moins une des valeurs est null, la comparaison produit null. Par ailleurs, l'utilisation de la méthode CLR `Equals` sur deux <xref:System.Data.SqlTypes> produira true si les deux sont null. Cela reflète la différence entre l'utilisation d'une méthode d'instance, telle que la méthode CLR `String.Equals`, et l'utilisation d'une méthode statique/partagée, `SqlString.Equals`.  
  
 L'exemple suivant montre la différence de résultats entre les méthodes `SqlString.Equals` et `String.Equals` lorsque chacune passe une paire de valeurs null puis une paire de chaînes vides.  
  
 [!code-csharp[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/VB/source.vb#1)]  
  
 Le code génère la sortie suivante :  
  
```  
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

- [Types de données SQL Server et ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)
- [Fournisseurs managés ADO.NET et centre de développement DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
