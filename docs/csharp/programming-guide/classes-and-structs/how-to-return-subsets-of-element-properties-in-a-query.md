---
title: Comment retourner des sous-ensembles de propriétés d’éléments dans une requête (Guide de programmation C#)
description: Découvrez comment utiliser un type anonyme dans une expression de requête en C# pour retourner certaines des propriétés de chaque élément source.
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: 5784d6a288af374d357346e32535ebe9c1877bcc
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97512793"
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a><span data-ttu-id="b2440-103">Comment retourner des sous-ensembles de propriétés d’éléments dans une requête (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="b2440-103">How to return subsets of element properties in a query (C# Programming Guide)</span></span>

<span data-ttu-id="b2440-104">Utilisez un type anonyme dans une expression de requête lorsque les deux conditions suivantes s’appliquent :</span><span class="sxs-lookup"><span data-stu-id="b2440-104">Use an anonymous type in a query expression when both of these conditions apply:</span></span>  
  
- <span data-ttu-id="b2440-105">Vous souhaitez retourner uniquement certaines propriétés de chaque élément source.</span><span class="sxs-lookup"><span data-stu-id="b2440-105">You want to return only some of the properties of each source element.</span></span>  
  
- <span data-ttu-id="b2440-106">Vous n’avez pas besoin de stocker les résultats de requête en dehors de la portée de la méthode dans laquelle la requête est exécutée.</span><span class="sxs-lookup"><span data-stu-id="b2440-106">You do not have to store the query results outside the scope of the method in which the query is executed.</span></span>  
  
 <span data-ttu-id="b2440-107">Si vous souhaitez uniquement retourner une propriété ou un champ de chaque élément source, vous pouvez utiliser l’opérateur point dans la clause `select`.</span><span class="sxs-lookup"><span data-stu-id="b2440-107">If you only want to return one property or field from each source element, then you can just use the dot operator in the `select` clause.</span></span> <span data-ttu-id="b2440-108">Par exemple, pour retourner uniquement l’`ID` de chaque `student`, écrivez la clause `select` de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="b2440-108">For example, to return only the `ID` of each `student`, write the `select` clause as follows:</span></span>  
  
```csharp  
select student.ID;  
```  
  
## <a name="example"></a><span data-ttu-id="b2440-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="b2440-109">Example</span></span>  

 <span data-ttu-id="b2440-110">L’exemple suivant montre comment utiliser un type anonyme pour retourner uniquement un sous-ensemble des propriétés de chaque élément source qui répond à la condition spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b2440-110">The following example shows how to use an anonymous type to return only a subset of the properties of each source element that matches the specified condition.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#31)]  
  
 <span data-ttu-id="b2440-111">Notez que le type anonyme utilise les noms de l’élément source pour ses propriétés si aucun nom n’est spécifié.</span><span class="sxs-lookup"><span data-stu-id="b2440-111">Note that the anonymous type uses the source element's names for its properties if no names are specified.</span></span> <span data-ttu-id="b2440-112">Pour attribuer de nouveaux noms aux propriétés du type anonyme, écrivez l’instruction `select` de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="b2440-112">To give new names to the properties in the anonymous type, write the `select` statement as follows:</span></span>  
  
```csharp  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 <span data-ttu-id="b2440-113">Si vous effectuez cette opération dans l’exemple précédent, l’instruction `Console.WriteLine` doit également changer :</span><span class="sxs-lookup"><span data-stu-id="b2440-113">If you try this in the previous example, then the `Console.WriteLine` statement must also change:</span></span>  
  
```csharp  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b2440-114">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="b2440-114">Compiling the Code</span></span>  
  
<span data-ttu-id="b2440-115">Pour exécuter ce code, copiez et collez la classe dans une application console C# avec une directive `using` pour System.Linq.</span><span class="sxs-lookup"><span data-stu-id="b2440-115">To run this code, copy and paste the class into a C# console application  with a `using` directive for System.Linq.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b2440-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b2440-116">See also</span></span>

- [<span data-ttu-id="b2440-117">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="b2440-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b2440-118">Types anonymes</span><span class="sxs-lookup"><span data-stu-id="b2440-118">Anonymous Types</span></span>](./anonymous-types.md)
- [<span data-ttu-id="b2440-119">LINQ en C#</span><span class="sxs-lookup"><span data-stu-id="b2440-119">LINQ in C#</span></span>](../../linq/index.md)
