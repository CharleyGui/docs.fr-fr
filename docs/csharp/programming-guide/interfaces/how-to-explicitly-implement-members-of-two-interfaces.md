---
title: Comment implémenter explicitement des membres de deux interfaces (Guide de programmation C#)
description: Apprenez à implémenter explicitement deux interfaces qui ont les mêmes noms de membres et donnez à chaque membre d’interface une implémentation distincte dans cet exemple C#.
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [C#], explicitly implementing interface members
- interfaces [C#], explicitly implementing with inheritance
ms.assetid: 8b402ddc-dff9-4869-89cb-d718c764e68e
ms.openlocfilehash: d60ec43f734d5e8bfa7f467874440bd3514877fe
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303060"
---
# <a name="how-to-explicitly-implement-members-of-two-interfaces-c-programming-guide"></a><span data-ttu-id="873b3-103">Comment implémenter explicitement des membres de deux interfaces (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="873b3-103">How to explicitly implement members of two interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="873b3-104">L’implémentation explicite d’une [interface](../../language-reference/keywords/interface.md) permet également au programmeur d’implémenter deux interfaces qui ont les mêmes noms de membres et donnent à chaque membre d’interface une implémentation distincte.</span><span class="sxs-lookup"><span data-stu-id="873b3-104">Explicit [interface](../../language-reference/keywords/interface.md) implementation also allows the programmer to implement two interfaces that have the same member names and give each interface member a separate implementation.</span></span> <span data-ttu-id="873b3-105">L’exemple suivant affiche les dimensions d’une zone dans les unités de mesure à la fois métriques et britanniques.</span><span class="sxs-lookup"><span data-stu-id="873b3-105">This example displays the dimensions of a box in both metric and English units.</span></span> <span data-ttu-id="873b3-106">La [classe](../../language-reference/keywords/class.md) Box implémente deux interfaces, IEnglishDimensions et IMetricDimensions, qui représentent les différents systèmes de mesure.</span><span class="sxs-lookup"><span data-stu-id="873b3-106">The Box [class](../../language-reference/keywords/class.md) implements two interfaces IEnglishDimensions and IMetricDimensions, which represent the different measurement systems.</span></span> <span data-ttu-id="873b3-107">Les deux interfaces ont des noms de membres identiques, Length et Width.</span><span class="sxs-lookup"><span data-stu-id="873b3-107">Both interfaces have identical member names, Length and Width.</span></span>  
  
## <a name="example"></a><span data-ttu-id="873b3-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="873b3-108">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#9)]  
  
## <a name="robust-programming"></a><span data-ttu-id="873b3-109">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="873b3-109">Robust Programming</span></span>  
 <span data-ttu-id="873b3-110">Si vous souhaitez utiliser par défaut les unités de mesure britanniques, implémentez les méthodes Length et Width normalement, puis implémentez explicitement les méthodes Length et Width à partir de l’interface IMetricDimensions :</span><span class="sxs-lookup"><span data-stu-id="873b3-110">If you want to make the default measurements in English units, implement the methods Length and Width normally, and explicitly implement the Length and Width methods from the IMetricDimensions interface:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#10)]  
  
 <span data-ttu-id="873b3-111">Dans ce cas, vous pouvez accéder aux unités de mesure britanniques à partir de l’instance de classe et accéder aux unités métriques à partir de l’instance d’interface :</span><span class="sxs-lookup"><span data-stu-id="873b3-111">In this case, you can access the English units from the class instance and access the metric units from the interface instance:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="873b3-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="873b3-112">See also</span></span>

- [<span data-ttu-id="873b3-113">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="873b3-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="873b3-114">Classes et structs</span><span class="sxs-lookup"><span data-stu-id="873b3-114">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="873b3-115">Interfaces</span><span class="sxs-lookup"><span data-stu-id="873b3-115">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="873b3-116">Comment implémenter explicitement des membres d’interface</span><span class="sxs-lookup"><span data-stu-id="873b3-116">How to explicitly implement interface members</span></span>](./how-to-explicitly-implement-interface-members.md)
