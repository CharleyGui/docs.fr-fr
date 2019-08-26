---
title: 'Procédure : Implémenter de manière explicite des membres de deux interfaces - Guide de programmation C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [C#], explicitly implementing interface members
- interfaces [C#], explicitly implementing with inheritance
ms.assetid: 8b402ddc-dff9-4869-89cb-d718c764e68e
ms.openlocfilehash: 1d4dd0485be1d859e3e9594ab1558a907b8f1f7a
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589191"
---
# <a name="how-to-explicitly-implement-members-of-two-interfaces-c-programming-guide"></a><span data-ttu-id="0a829-102">Procédure : Implémenter de manière explicite des membres de deux interfaces (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="0a829-102">How to: Explicitly Implement Members of Two Interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="0a829-103">L’implémentation explicite d’une [interface](../../language-reference/keywords/interface.md) permet également au programmeur d’implémenter deux interfaces qui ont les mêmes noms de membres et donnent à chaque membre d’interface une implémentation distincte.</span><span class="sxs-lookup"><span data-stu-id="0a829-103">Explicit [interface](../../language-reference/keywords/interface.md) implementation also allows the programmer to implement two interfaces that have the same member names and give each interface member a separate implementation.</span></span> <span data-ttu-id="0a829-104">L’exemple suivant affiche les dimensions d’une zone dans les unités de mesure à la fois métriques et britanniques.</span><span class="sxs-lookup"><span data-stu-id="0a829-104">This example displays the dimensions of a box in both metric and English units.</span></span> <span data-ttu-id="0a829-105">La [classe](../../language-reference/keywords/class.md) Box implémente deux interfaces, IEnglishDimensions et IMetricDimensions, qui représentent les différents systèmes de mesure.</span><span class="sxs-lookup"><span data-stu-id="0a829-105">The Box [class](../../language-reference/keywords/class.md) implements two interfaces IEnglishDimensions and IMetricDimensions, which represent the different measurement systems.</span></span> <span data-ttu-id="0a829-106">Les deux interfaces ont des noms de membres identiques, Length et Width.</span><span class="sxs-lookup"><span data-stu-id="0a829-106">Both interfaces have identical member names, Length and Width.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a829-107">Exemples</span><span class="sxs-lookup"><span data-stu-id="0a829-107">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#9)]  
  
## <a name="robust-programming"></a><span data-ttu-id="0a829-108">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="0a829-108">Robust Programming</span></span>  
 <span data-ttu-id="0a829-109">Si vous souhaitez utiliser par défaut les unités de mesure britanniques, implémentez les méthodes Length et Width normalement, puis implémentez explicitement les méthodes Length et Width à partir de l’interface IMetricDimensions :</span><span class="sxs-lookup"><span data-stu-id="0a829-109">If you want to make the default measurements in English units, implement the methods Length and Width normally, and explicitly implement the Length and Width methods from the IMetricDimensions interface:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#10)]  
  
 <span data-ttu-id="0a829-110">Dans ce cas, vous pouvez accéder aux unités de mesure britanniques à partir de l’instance de classe et accéder aux unités métriques à partir de l’instance d’interface :</span><span class="sxs-lookup"><span data-stu-id="0a829-110">In this case, you can access the English units from the class instance and access the metric units from the interface instance:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="0a829-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0a829-111">See also</span></span>

- [<span data-ttu-id="0a829-112">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="0a829-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="0a829-113">Classes et structs</span><span class="sxs-lookup"><span data-stu-id="0a829-113">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="0a829-114">Interfaces</span><span class="sxs-lookup"><span data-stu-id="0a829-114">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="0a829-115">Guide pratique pour implémenter de manière explicite des membres d’interface</span><span class="sxs-lookup"><span data-stu-id="0a829-115">How to: Explicitly Implement Interface Members</span></span>](./how-to-explicitly-implement-interface-members.md)
