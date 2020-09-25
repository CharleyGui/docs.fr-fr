---
title: Comment implémenter explicitement des membres de deux interfaces (Guide de programmation C#)
description: Apprenez à implémenter explicitement deux interfaces qui ont les mêmes noms de membres et donnez à chaque membre d’interface une implémentation distincte dans cet exemple C#.
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [C#], explicitly implementing interface members
- interfaces [C#], explicitly implementing with inheritance
ms.assetid: 8b402ddc-dff9-4869-89cb-d718c764e68e
ms.openlocfilehash: 18b1f9cfb1690d35c0bca0a3c79c1b80ae5dd44d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91205085"
---
# <a name="how-to-explicitly-implement-members-of-two-interfaces-c-programming-guide"></a><span data-ttu-id="42883-103">Comment implémenter explicitement des membres de deux interfaces (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="42883-103">How to explicitly implement members of two interfaces (C# Programming Guide)</span></span>

<span data-ttu-id="42883-104">L’implémentation explicite d’une [interface](../../language-reference/keywords/interface.md) permet également au programmeur d’implémenter deux interfaces qui ont les mêmes noms de membres et donnent à chaque membre d’interface une implémentation distincte.</span><span class="sxs-lookup"><span data-stu-id="42883-104">Explicit [interface](../../language-reference/keywords/interface.md) implementation also allows the programmer to implement two interfaces that have the same member names and give each interface member a separate implementation.</span></span> <span data-ttu-id="42883-105">L’exemple suivant affiche les dimensions d’une zone dans les unités de mesure à la fois métriques et britanniques.</span><span class="sxs-lookup"><span data-stu-id="42883-105">This example displays the dimensions of a box in both metric and English units.</span></span> <span data-ttu-id="42883-106">La [classe](../../language-reference/keywords/class.md) Box implémente deux interfaces, IEnglishDimensions et IMetricDimensions, qui représentent les différents systèmes de mesure.</span><span class="sxs-lookup"><span data-stu-id="42883-106">The Box [class](../../language-reference/keywords/class.md) implements two interfaces IEnglishDimensions and IMetricDimensions, which represent the different measurement systems.</span></span> <span data-ttu-id="42883-107">Les deux interfaces ont des noms de membres identiques, Length et Width.</span><span class="sxs-lookup"><span data-stu-id="42883-107">Both interfaces have identical member names, Length and Width.</span></span>  
  
## <a name="example"></a><span data-ttu-id="42883-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="42883-108">Example</span></span>  

 [!code-csharp[csProgGuideInheritance#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#9)]  
  
## <a name="robust-programming"></a><span data-ttu-id="42883-109">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="42883-109">Robust Programming</span></span>  

 <span data-ttu-id="42883-110">Si vous souhaitez utiliser par défaut les unités de mesure britanniques, implémentez les méthodes Length et Width normalement, puis implémentez explicitement les méthodes Length et Width à partir de l’interface IMetricDimensions :</span><span class="sxs-lookup"><span data-stu-id="42883-110">If you want to make the default measurements in English units, implement the methods Length and Width normally, and explicitly implement the Length and Width methods from the IMetricDimensions interface:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#10)]  
  
 <span data-ttu-id="42883-111">Dans ce cas, vous pouvez accéder aux unités de mesure britanniques à partir de l’instance de classe et accéder aux unités métriques à partir de l’instance d’interface :</span><span class="sxs-lookup"><span data-stu-id="42883-111">In this case, you can access the English units from the class instance and access the metric units from the interface instance:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="42883-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="42883-112">See also</span></span>

- [<span data-ttu-id="42883-113">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="42883-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="42883-114">Classes et structs</span><span class="sxs-lookup"><span data-stu-id="42883-114">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="42883-115">Interfaces</span><span class="sxs-lookup"><span data-stu-id="42883-115">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="42883-116">Comment implémenter explicitement des membres d’interface</span><span class="sxs-lookup"><span data-stu-id="42883-116">How to explicitly implement interface members</span></span>](./how-to-explicitly-implement-interface-members.md)
