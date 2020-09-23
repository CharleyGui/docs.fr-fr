---
title: Regroupement de données
ms.date: 07/20/2015
ms.assetid: 8f3a0871-6958-4aef-8f6f-493e189fd57d
ms.openlocfilehash: aae48543472ee71990d0bc96defa9ad6a6ab4c0d
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91084201"
---
# <a name="grouping-data-visual-basic"></a>Regroupement de données (Visual Basic)

Le regroupement consiste à placer des données dans des groupes afin que les éléments de chaque groupe partagent un attribut commun.  
  
 L’illustration suivante montre les résultats du regroupement d’une séquence de caractères. La clé de chaque groupe est le caractère.  
  
 ![Diagramme illustrant une opération de regroupement LINQ.](./media/grouping-data/linq-group-operation.png)  
  
 Les méthodes d’opérateurs de requête standard qui regroupent les éléments de données sont répertoriées dans la section suivante.  
  
## <a name="methods"></a>Méthodes  
  
|Nom de la méthode|Description|Syntaxe des expressions de requête Visual Basic|Informations complémentaires|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|GroupBy|Regroupe les éléments qui partagent un attribut commun. Chaque groupe est représenté par un objet <xref:System.Linq.IGrouping%602>.|`Group … By … Into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|ToLookup|Insère des éléments dans un <xref:System.Linq.Lookup%602> (un dictionnaire de type un-à-plusieurs) basé sur une fonction de sélecteur de clés.|Non applicable.|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a>Exemple de syntaxe d’expression de requête  

 L’exemple de code suivant utilise la clause `Group By` pour regrouper des entiers dans une liste selon qu’ils sont pairs ou impairs.  
  
```vb  
Dim numbers As New System.Collections.Generic.List(Of Integer)(  
     New Integer() {35, 44, 200, 84, 3987, 4, 199, 329, 446, 208})  
  
Dim query = From number In numbers
            Group By Remainder = (number Mod 2) Into Group  
  
Dim sb As New System.Text.StringBuilder()  
For Each group In query  
    sb.AppendLine(If(group.Remainder = 0, vbCrLf & "Even numbers:", vbCrLf & "Odd numbers:"))  
    For Each num In group.Group  
        sb.AppendLine(num)  
    Next  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' Odd numbers:  
' 35  
' 3987  
' 199  
' 329  
  
' Even numbers:  
' 44  
' 200  
' 84  
' 4  
' 446  
' 208  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Linq>
- [Vue d’ensemble des opérateurs de requête standard (Visual Basic)](standard-query-operators-overview.md)
- [Group By (clause)](../../../language-reference/queries/group-by-clause.md)
- [Comment : regrouper des fichiers par extension (LINQ) (Visual Basic)](how-to-group-files-by-extension-linq.md)
- [Comment : fractionner un fichier en plusieurs fichiers à l’aide de groupes (LINQ) (Visual Basic)](how-to-split-a-file-into-many-files-by-using-groups-linq.md)
