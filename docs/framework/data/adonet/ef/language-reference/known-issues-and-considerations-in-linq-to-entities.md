---
title: Problèmes connus et éléments à prendre en compte dans LINQ to Entities
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: acd71129-5ff0-4b4e-b266-c72cc0c53601
ms.openlocfilehash: 303e46e79786ce7f062db4a1a3ffb6c321169af8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64631303"
---
# <a name="known-issues-and-considerations-in-linq-to-entities"></a>Problèmes connus et éléments à prendre en compte dans LINQ to Entities
Cette section fournit des informations sur les problèmes connus au niveau des requêtes [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)].  
  
- [Requêtes LINQ qui ne peut pas être mis en cache](#LINQQueriesThatAreNotCached)  
  
- [Perte des informations de classement](#OrderingInfoLost)  
  
- [Entiers non signés non pris en charge.](#UnsignedIntsUnsupported)  
  
- [Erreurs de Conversion de type](#TypeConversionErrors)  
  
- [Référencement des Variables Non scalaires non pris en charge.](#RefNonScalarClosures)  
  
- [Requêtes imbriquées peuvent échouer avec SQL Server 2000](#NestedQueriesSQL2000)  
  
- [Projection dans un Type anonyme](#ProjectToAnonymousType)  
  
<a name="LINQQueriesThatAreNotCached"></a>   
## <a name="linq-queries-that-cannot-be-cached"></a>Requêtes LINQ qui ne peuvent pas être mises en cache  
 Depuis le .NET Framework 4.5, les requêtes LINQ to Entities sont automatiquement mises en cache. Cependant, les requêtes LINQ to Entities qui appliquent l’opérateur `Enumerable.Contains` aux collections en mémoire ne sont pas automatiquement mises en cache. Le paramétrage des collections en mémoire dans les requêtes LINQ compilées n’est pas autorisé.  
  
<a name="OrderingInfoLost"></a>   
## <a name="ordering-information-lost"></a>Perte des informations de tri  
 La projection de colonnes dans un type anonyme entraînera la perte des informations de tri dans certains requêtes exécutées sur une base de données [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)] définie à un niveau de compatibilité de « 80 ».  Cela se produit lorsqu'un nom de colonne figurant dans la liste Order by correspond à un nom de colonne dans le sélecteur, comme l'illustre l'exemple suivant :  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt543840)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt543840)]  
  
<a name="UnsignedIntsUnsupported"></a>   
## <a name="unsigned-integers-not-supported"></a>Entiers non signés non pris en charge  
 La définition d'un type d'entier non signé dans une requête [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] n'est pas prise en charge, car [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] ne prend pas en charge les entiers non signés. Si vous spécifiez un entier non signé, un <xref:System.ArgumentException> exception est levée pendant la traduction d’expression de requête, comme illustré dans l’exemple suivant. Dans cet exemple, la requête vise à extraire une commande dont le numéro est 48000.  
  
 [!code-csharp[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#uintasqueryparam)]
 [!code-vb[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#uintasqueryparam)]  
  
<a name="TypeConversionErrors"></a>   
## <a name="type-conversion-errors"></a>Erreurs de conversion de type  
 En Visual Basic, lorsqu'une propriété est mappée à une colonne de type bit SQL Server avec une valeur de 1 à l'aide de la fonction `CByte`, une exception <xref:System.Data.SqlClient.SqlException> est levée avec un message « Erreur de dépassement arithmétique ». L'exemple suivant interroge la colonne `Product.MakeFlag` dans l'exemple de base de données AdventureWorks et une exception est levée lorsque les résultats de la requête sont itérés.  
  
 [!code-vb[DP L2E Conceptual Examples#SBUDT544355](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt544355)]  
  
<a name="RefNonScalarClosures"></a>   
## <a name="referencing-non-scalar-variables-not-supported"></a>Référencement de variables non scalaires non pris en charge  
 Le référencement d'une variable non scalaire, telle qu'une entité, dans une requête n'est pas pris en charge. Lorsqu'une telle requête s'exécute, une exception <xref:System.NotSupportedException> est levée avec un message indiquant « Impossible de créer une valeur constante de type «`EntityType`. Seuls les types primitifs (« Int32, String et Guid ») sont pris en charge dans ce contexte. »  
  
> [!NOTE]
>  Le référencement d’une collection de variables scalaires est pris en charge.  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt555877)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt555877)]  
  
<a name="NestedQueriesSQL2000"></a>   
## <a name="nested-queries-may-fail-with-sql-server-2000"></a>Les requêtes imbriquées peuvent échouer avec SQL Server 2000  
 Avec SQL Server 2000, les requêtes LINQ to Entities peuvent échouer si elles produisent des requêtes Transact-SQL imbriquées qui ont trois niveaux ou plus de profondeur.  
  
<a name="ProjectToAnonymousType"></a>   
## <a name="projecting-to-an-anonymous-type"></a>Projection dans un type anonyme  
 Si vous définissez le chemin d’accès de votre requête initiale pour inclure des objets connexes à l’aide de la méthode <xref:System.Data.Objects.ObjectQuery%601.Include%2A> sur <xref:System.Data.Objects.ObjectQuery%601> et si vous utilisez LINQ pour projeter les objets retournés dans un type anonyme, les objets spécifiés dans la méthode d’inclusion ne sont pas inclus dans les résultats de la requête.  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype1)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype1)]  
  
 Pour obtenir des objets connexes, ne projetez pas les types retournés dans un type anonyme.  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype2)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype2)]  
  
## <a name="see-also"></a>Voir aussi

- [LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)
