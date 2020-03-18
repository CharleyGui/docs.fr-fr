---
title: Comment retourner les sous-ensembles de propriétés d’éléments dans une requête - Guide de programmation C
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: 27a2626fc46307a7195040adf746d8d8757d2f82
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714856"
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a><span data-ttu-id="d1c02-102">Comment retourner les sous-ensembles de propriétés d’éléments dans une requête (Guide de programmation C)</span><span class="sxs-lookup"><span data-stu-id="d1c02-102">How to return subsets of element properties in a query (C# Programming Guide)</span></span>
<span data-ttu-id="d1c02-103">Utilisez un type anonyme dans une expression de requête lorsque les deux conditions suivantes s’appliquent :</span><span class="sxs-lookup"><span data-stu-id="d1c02-103">Use an anonymous type in a query expression when both of these conditions apply:</span></span>  
  
- <span data-ttu-id="d1c02-104">Vous souhaitez retourner uniquement certaines propriétés de chaque élément source.</span><span class="sxs-lookup"><span data-stu-id="d1c02-104">You want to return only some of the properties of each source element.</span></span>  
  
- <span data-ttu-id="d1c02-105">Vous n’avez pas besoin de stocker les résultats de requête en dehors de la portée de la méthode dans laquelle la requête est exécutée.</span><span class="sxs-lookup"><span data-stu-id="d1c02-105">You do not have to store the query results outside the scope of the method in which the query is executed.</span></span>  
  
 <span data-ttu-id="d1c02-106">Si vous souhaitez uniquement retourner une propriété ou un champ de chaque élément source, vous pouvez utiliser l’opérateur point dans la clause `select`.</span><span class="sxs-lookup"><span data-stu-id="d1c02-106">If you only want to return one property or field from each source element, then you can just use the dot operator in the `select` clause.</span></span> <span data-ttu-id="d1c02-107">Par exemple, pour retourner uniquement l’`ID` de chaque `student`, écrivez la clause `select` de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="d1c02-107">For example, to return only the `ID` of each `student`, write the `select` clause as follows:</span></span>  
  
```csharp  
select student.ID;  
```  
  
## <a name="example"></a><span data-ttu-id="d1c02-108"> Exemple</span><span class="sxs-lookup"><span data-stu-id="d1c02-108">Example</span></span>  
 <span data-ttu-id="d1c02-109">L’exemple suivant montre comment utiliser un type anonyme pour retourner uniquement un sous-ensemble des propriétés de chaque élément source qui répond à la condition spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d1c02-109">The following example shows how to use an anonymous type to return only a subset of the properties of each source element that matches the specified condition.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#31)]  
  
 <span data-ttu-id="d1c02-110">Notez que le type anonyme utilise les noms de l’élément source pour ses propriétés si aucun nom n’est spécifié.</span><span class="sxs-lookup"><span data-stu-id="d1c02-110">Note that the anonymous type uses the source element's names for its properties if no names are specified.</span></span> <span data-ttu-id="d1c02-111">Pour attribuer de nouveaux noms aux propriétés du type anonyme, écrivez l’instruction `select` de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="d1c02-111">To give new names to the properties in the anonymous type, write the `select` statement as follows:</span></span>  
  
```csharp  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 <span data-ttu-id="d1c02-112">Si vous effectuez cette opération dans l’exemple précédent, l’instruction `Console.WriteLine` doit également changer :</span><span class="sxs-lookup"><span data-stu-id="d1c02-112">If you try this in the previous example, then the `Console.WriteLine` statement must also change:</span></span>  
  
```csharp  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d1c02-113">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="d1c02-113">Compiling the Code</span></span>  
  
<span data-ttu-id="d1c02-114">Pour exécuter ce code, copiez et collez la classe dans une application console C# avec une directive `using` pour System.Linq.</span><span class="sxs-lookup"><span data-stu-id="d1c02-114">To run this code, copy and paste the class into a C# console application  with a `using` directive for System.Linq.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d1c02-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d1c02-115">See also</span></span>

- [<span data-ttu-id="d1c02-116">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="d1c02-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d1c02-117">Types anonymes</span><span class="sxs-lookup"><span data-stu-id="d1c02-117">Anonymous Types</span></span>](./anonymous-types.md)
- [<span data-ttu-id="d1c02-118">LINQ en C#</span><span class="sxs-lookup"><span data-stu-id="d1c02-118">LINQ in C#</span></span>](../../linq/index.md)
