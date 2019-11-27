---
title: Regroupement de données
ms.date: 07/20/2015
ms.assetid: 8f3a0871-6958-4aef-8f6f-493e189fd57d
ms.openlocfilehash: 6e84ccfbd6a2193ac5ab368d7526da2de29a3c47
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353389"
---
# <a name="grouping-data-visual-basic"></a><span data-ttu-id="9c8b5-102">Regroupement de données (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9c8b5-102">Grouping Data (Visual Basic)</span></span>
<span data-ttu-id="9c8b5-103">Le regroupement consiste à placer des données dans des groupes afin que les éléments de chaque groupe partagent un attribut commun.</span><span class="sxs-lookup"><span data-stu-id="9c8b5-103">Grouping refers to the operation of putting data into groups so that the elements in each group share a common attribute.</span></span>  
  
 <span data-ttu-id="9c8b5-104">L’illustration suivante montre les résultats du regroupement d’une séquence de caractères.</span><span class="sxs-lookup"><span data-stu-id="9c8b5-104">The following illustration shows the results of grouping a sequence of characters.</span></span> <span data-ttu-id="9c8b5-105">La clé de chaque groupe est le caractère.</span><span class="sxs-lookup"><span data-stu-id="9c8b5-105">The key for each group is the character.</span></span>  
  
 ![Diagramme illustrant une opération de regroupement LINQ.](./media/grouping-data/linq-group-operation.png)  
  
 <span data-ttu-id="9c8b5-107">Les méthodes d’opérateurs de requête standard qui regroupent les éléments de données sont répertoriées dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="9c8b5-107">The standard query operator methods that group data elements are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9c8b5-108">Méthodes</span><span class="sxs-lookup"><span data-stu-id="9c8b5-108">Methods</span></span>  
  
|<span data-ttu-id="9c8b5-109">Nom de la méthode</span><span class="sxs-lookup"><span data-stu-id="9c8b5-109">Method Name</span></span>|<span data-ttu-id="9c8b5-110">Description</span><span class="sxs-lookup"><span data-stu-id="9c8b5-110">Description</span></span>|<span data-ttu-id="9c8b5-111">Syntaxe des expressions de requête Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9c8b5-111">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="9c8b5-112">Informations supplémentaires</span><span class="sxs-lookup"><span data-stu-id="9c8b5-112">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="9c8b5-113">GroupBy</span><span class="sxs-lookup"><span data-stu-id="9c8b5-113">GroupBy</span></span>|<span data-ttu-id="9c8b5-114">Regroupe les éléments qui partagent un attribut commun.</span><span class="sxs-lookup"><span data-stu-id="9c8b5-114">Groups elements that share a common attribute.</span></span> <span data-ttu-id="9c8b5-115">Chaque groupe est représenté par un objet <xref:System.Linq.IGrouping%602>.</span><span class="sxs-lookup"><span data-stu-id="9c8b5-115">Each group is represented by an <xref:System.Linq.IGrouping%602> object.</span></span>|`Group … By … Into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="9c8b5-116">ToLookup</span><span class="sxs-lookup"><span data-stu-id="9c8b5-116">ToLookup</span></span>|<span data-ttu-id="9c8b5-117">Insère des éléments dans un <xref:System.Linq.Lookup%602> (un dictionnaire de type un-à-plusieurs) basé sur une fonction de sélecteur de clés.</span><span class="sxs-lookup"><span data-stu-id="9c8b5-117">Inserts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span>|<span data-ttu-id="9c8b5-118">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="9c8b5-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="9c8b5-119">Exemple de syntaxe d’expression de requête</span><span class="sxs-lookup"><span data-stu-id="9c8b5-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="9c8b5-120">L’exemple de code suivant utilise la clause `Group By` pour regrouper des entiers dans une liste selon qu’ils sont pairs ou impairs.</span><span class="sxs-lookup"><span data-stu-id="9c8b5-120">The following code example uses the `Group By` clause to group integers in a list according to whether they are even or odd.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9c8b5-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9c8b5-121">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="9c8b5-122">Vue d’ensemble des opérateurs de requête standard (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9c8b5-122">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="9c8b5-123">Group By (clause)</span><span class="sxs-lookup"><span data-stu-id="9c8b5-123">Group By Clause</span></span>](../../../../visual-basic/language-reference/queries/group-by-clause.md)
- [<span data-ttu-id="9c8b5-124">Comment : regrouper des fichiers par extension (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9c8b5-124">How to: Group Files by Extension (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)
- [<span data-ttu-id="9c8b5-125">Comment : fractionner un fichier en plusieurs fichiers à l’aide de groupes (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9c8b5-125">How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
