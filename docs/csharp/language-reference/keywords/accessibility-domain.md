---
description: Domaine d'accessibilité - Référence C#
title: Domaine d'accessibilité - Référence C#
ms.date: 07/20/2015
helpviewer_keywords:
- accessibility domain [C#]
ms.assetid: 8af779c1-275b-44be-a864-9edfbca71bcc
ms.openlocfilehash: 2cfc4cc72a79b33276b7d822a2b31eb518dcf784
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89127059"
---
# <a name="accessibility-domain-c-reference"></a><span data-ttu-id="c5fc9-103">Domaine d'accessibilité (référence C#)</span><span class="sxs-lookup"><span data-stu-id="c5fc9-103">Accessibility Domain (C# Reference)</span></span>
<span data-ttu-id="c5fc9-104">Le domaine d’accessibilité d’un membre indique dans quelles sections du programme un membre peut être référencé.</span><span class="sxs-lookup"><span data-stu-id="c5fc9-104">The accessibility domain of a member specifies in which program sections a member can be referenced.</span></span> <span data-ttu-id="c5fc9-105">Si le membre est imbriqué dans un autre type, son domaine d’accessibilité est déterminé à la fois par le [niveau d’accessibilité](./accessibility-levels.md) du membre et par le domaine d’accessibilité du type conteneur immédiat.</span><span class="sxs-lookup"><span data-stu-id="c5fc9-105">If the member is nested within another type, its accessibility domain is determined by both the [accessibility level](./accessibility-levels.md) of the member and the accessibility domain of the immediately containing type.</span></span>  
  
 <span data-ttu-id="c5fc9-106">Le domaine d’accessibilité d’un type de niveau supérieur est au moins le texte du programme du projet dans lequel il est déclaré.</span><span class="sxs-lookup"><span data-stu-id="c5fc9-106">The accessibility domain of a top-level type is at least the program text of the project that it is declared in.</span></span> <span data-ttu-id="c5fc9-107">Cela signifie que le domaine inclut tous les fichiers sources de ce projet.</span><span class="sxs-lookup"><span data-stu-id="c5fc9-107">That is, the domain includes all of the source files of this project.</span></span> <span data-ttu-id="c5fc9-108">Le domaine d’accessibilité d’un type imbriqué est au moins le texte de programme du type dans lequel il est déclaré.</span><span class="sxs-lookup"><span data-stu-id="c5fc9-108">The accessibility domain of a nested type is at least the program text of the type in which it is declared.</span></span> <span data-ttu-id="c5fc9-109">Autrement dit, le domaine est le corps du type, qui inclut tous les types imbriqués.</span><span class="sxs-lookup"><span data-stu-id="c5fc9-109">That is, the domain is the type body, which includes all nested types.</span></span> <span data-ttu-id="c5fc9-110">Le domaine d’accessibilité d’un type imbriqué ne dépasse jamais celui du type conteneur.</span><span class="sxs-lookup"><span data-stu-id="c5fc9-110">The accessibility domain of a nested type never exceeds that of the containing type.</span></span> <span data-ttu-id="c5fc9-111">Ces concepts sont illustrés dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="c5fc9-111">These concepts are demonstrated in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5fc9-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="c5fc9-112">Example</span></span>  
 <span data-ttu-id="c5fc9-113">Cet exemple comporte un type de niveau supérieur, `T1`, et deux classes imbriquées, `M1` et `M2`.</span><span class="sxs-lookup"><span data-stu-id="c5fc9-113">This example contains a top-level type, `T1`, and two nested classes, `M1` and `M2`.</span></span> <span data-ttu-id="c5fc9-114">Les classes contiennent des champs qui ont des accessibilités déclarées différentes.</span><span class="sxs-lookup"><span data-stu-id="c5fc9-114">The classes contain fields that have different declared accessibilities.</span></span> <span data-ttu-id="c5fc9-115">Dans la méthode `Main`, un commentaire suit chaque instruction pour indiquer le domaine d’accessibilité de chaque membre.</span><span class="sxs-lookup"><span data-stu-id="c5fc9-115">In the `Main` method, a comment follows each statement to indicate the accessibility domain of each member.</span></span> <span data-ttu-id="c5fc9-116">Notez que les instructions qui essaient de référencer les membres inaccessibles sont commentées. Si vous souhaitez voir les erreurs de compilation provoquées par le référencement d’un membre inaccessible, supprimez les commentaires un par un.</span><span class="sxs-lookup"><span data-stu-id="c5fc9-116">Notice that the statements that try to reference the inaccessible members are commented out. If you want to see the compiler errors caused by referencing an inaccessible member, remove the comments one at a time.</span></span>  
  
[!code-csharp[csrefKeywordsModifiers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#4)]
  
## <a name="c-language-specification"></a><span data-ttu-id="c5fc9-117">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="c5fc9-117">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c5fc9-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c5fc9-118">See also</span></span>

- [<span data-ttu-id="c5fc9-119">Référence C#</span><span class="sxs-lookup"><span data-stu-id="c5fc9-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c5fc9-120">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="c5fc9-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c5fc9-121">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="c5fc9-121">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="c5fc9-122">Modificateurs d’accès</span><span class="sxs-lookup"><span data-stu-id="c5fc9-122">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="c5fc9-123">Niveaux d'accessibilité</span><span class="sxs-lookup"><span data-stu-id="c5fc9-123">Accessibility Levels</span></span>](./accessibility-levels.md)
- [<span data-ttu-id="c5fc9-124">Restrictions concernant l’utilisation des niveaux d’accessibilité</span><span class="sxs-lookup"><span data-stu-id="c5fc9-124">Restrictions on Using Accessibility Levels</span></span>](./restrictions-on-using-accessibility-levels.md)
- [<span data-ttu-id="c5fc9-125">Modificateurs d’accès</span><span class="sxs-lookup"><span data-stu-id="c5fc9-125">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="c5fc9-126">public</span><span class="sxs-lookup"><span data-stu-id="c5fc9-126">public</span></span>](./public.md)
- [<span data-ttu-id="c5fc9-127">priv</span><span class="sxs-lookup"><span data-stu-id="c5fc9-127">private</span></span>](./private.md)
- [<span data-ttu-id="c5fc9-128">protected</span><span class="sxs-lookup"><span data-stu-id="c5fc9-128">protected</span></span>](./protected.md)
- [<span data-ttu-id="c5fc9-129">intérieurs</span><span class="sxs-lookup"><span data-stu-id="c5fc9-129">internal</span></span>](./internal.md)
