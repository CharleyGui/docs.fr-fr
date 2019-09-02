---
title: "Procédure : Retourner des sous-ensembles de propriétés d'éléments dans une requête - Guide de programmation C#"
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: 2c9fea2189819058187020c2e67b8826659fbed4
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205444"
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a><span data-ttu-id="f4052-102">Procédure : Retourner des sous-ensembles de propriétés d'éléments dans une requête (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="f4052-102">How to: Return Subsets of Element Properties in a Query (C# Programming Guide)</span></span>
<span data-ttu-id="f4052-103">Utilisez un type anonyme dans une expression de requête lorsque les deux conditions suivantes s’appliquent :</span><span class="sxs-lookup"><span data-stu-id="f4052-103">Use an anonymous type in a query expression when both of these conditions apply:</span></span>  
  
- <span data-ttu-id="f4052-104">Vous souhaitez retourner uniquement certaines propriétés de chaque élément source.</span><span class="sxs-lookup"><span data-stu-id="f4052-104">You want to return only some of the properties of each source element.</span></span>  
  
- <span data-ttu-id="f4052-105">Vous n’avez pas besoin de stocker les résultats de requête en dehors de la portée de la méthode dans laquelle la requête est exécutée.</span><span class="sxs-lookup"><span data-stu-id="f4052-105">You do not have to store the query results outside the scope of the method in which the query is executed.</span></span>  
  
 <span data-ttu-id="f4052-106">Si vous souhaitez uniquement retourner une propriété ou un champ de chaque élément source, vous pouvez utiliser l’opérateur point dans la clause `select`.</span><span class="sxs-lookup"><span data-stu-id="f4052-106">If you only want to return one property or field from each source element, then you can just use the dot operator in the `select` clause.</span></span> <span data-ttu-id="f4052-107">Par exemple, pour retourner uniquement l’`ID` de chaque `student`, écrivez la clause `select` de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="f4052-107">For example, to return only the `ID` of each `student`, write the `select` clause as follows:</span></span>  
  
```csharp  
select student.ID;  
```  
  
## <a name="example"></a><span data-ttu-id="f4052-108">Exemples</span><span class="sxs-lookup"><span data-stu-id="f4052-108">Example</span></span>  
 <span data-ttu-id="f4052-109">L’exemple suivant montre comment utiliser un type anonyme pour retourner uniquement un sous-ensemble des propriétés de chaque élément source qui répond à la condition spécifiée.</span><span class="sxs-lookup"><span data-stu-id="f4052-109">The following example shows how to use an anonymous type to return only a subset of the properties of each source element that matches the specified condition.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#31)]  
  
 <span data-ttu-id="f4052-110">Notez que le type anonyme utilise les noms de l’élément source pour ses propriétés si aucun nom n’est spécifié.</span><span class="sxs-lookup"><span data-stu-id="f4052-110">Note that the anonymous type uses the source element's names for its properties if no names are specified.</span></span> <span data-ttu-id="f4052-111">Pour attribuer de nouveaux noms aux propriétés du type anonyme, écrivez l’instruction `select` de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="f4052-111">To give new names to the properties in the anonymous type, write the `select` statement as follows:</span></span>  
  
```csharp  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 <span data-ttu-id="f4052-112">Si vous effectuez cette opération dans l’exemple précédent, l’instruction `Console.WriteLine` doit également changer :</span><span class="sxs-lookup"><span data-stu-id="f4052-112">If you try this in the previous example, then the `Console.WriteLine` statement must also change:</span></span>  
  
```csharp  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f4052-113">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="f4052-113">Compiling the Code</span></span>  
  
<span data-ttu-id="f4052-114">Pour exécuter ce code, copiez et collez la classe dans une application console C# avec une directive `using` pour System.Linq.</span><span class="sxs-lookup"><span data-stu-id="f4052-114">To run this code, copy and paste the class into a C# console application  with a `using` directive for System.Linq.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f4052-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f4052-115">See also</span></span>

- [<span data-ttu-id="f4052-116">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="f4052-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="f4052-117">Types anonymes</span><span class="sxs-lookup"><span data-stu-id="f4052-117">Anonymous Types</span></span>](./anonymous-types.md)
- [<span data-ttu-id="f4052-118">Expressions de requête LINQ</span><span class="sxs-lookup"><span data-stu-id="f4052-118">LINQ Query Expressions</span></span>](../linq-query-expressions/index.md)
