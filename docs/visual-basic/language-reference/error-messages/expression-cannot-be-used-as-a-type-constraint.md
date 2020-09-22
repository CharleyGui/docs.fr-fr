---
title: "'<expression>' ne peut pas être utilisé en tant que contrainte de type"
ms.date: 07/20/2015
f1_keywords:
- bc32061
- vbc32061
helpviewer_keywords:
- BC32061
ms.assetid: b17821b7-fa14-4397-a211-6e2a14079f09
ms.openlocfilehash: 4f1db6bdbe6f25d0362b55acd95e716fbc2417ed
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874273"
---
# <a name="expression-cannot-be-used-as-a-type-constraint"></a><span data-ttu-id="b2654-102">'\<expression>' ne peut pas être utilisé en tant que contrainte de type</span><span class="sxs-lookup"><span data-stu-id="b2654-102">'\<expression>' cannot be used as a type constraint</span></span>

<span data-ttu-id="b2654-103">Une liste de contraintes contient une expression qui ne représente pas une contrainte valide sur un paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="b2654-103">A constraint list includes an expression that does not represent a valid constraint on a type parameter.</span></span>  
  
 <span data-ttu-id="b2654-104">Une liste de contraintes impose des exigences sur l’argument de type passé au paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="b2654-104">A constraint list imposes requirements on the type argument passed to the type parameter.</span></span> <span data-ttu-id="b2654-105">Vous pouvez spécifier les exigences suivantes dans toute combinaison :</span><span class="sxs-lookup"><span data-stu-id="b2654-105">You can specify the following requirements in any combination:</span></span>  
  
- <span data-ttu-id="b2654-106">L’argument de type doit implémenter une ou plusieurs interfaces</span><span class="sxs-lookup"><span data-stu-id="b2654-106">The type argument must implement one or more interfaces</span></span>  
  
- <span data-ttu-id="b2654-107">L’argument de type doit hériter d’une classe au plus</span><span class="sxs-lookup"><span data-stu-id="b2654-107">The type argument must inherit from at most one class</span></span>  
  
- <span data-ttu-id="b2654-108">L’argument de type doit exposer un constructeur sans paramètre accessible par le code de création (ajoutez la contrainte `New` )</span><span class="sxs-lookup"><span data-stu-id="b2654-108">The type argument must expose a parameterless constructor that the creating code can access (include the `New` constraint)</span></span>  
  
 <span data-ttu-id="b2654-109">Si vous n’incluez pas de classe ni d’interface spécifique dans la liste de contraintes, vous pouvez imposer une condition plus générale en spécifiant l’une des obligations suivantes :</span><span class="sxs-lookup"><span data-stu-id="b2654-109">If you do not include any specific class or interface in the constraint list, you can impose a more general requirement by specifying one of the following:</span></span>  
  
- <span data-ttu-id="b2654-110">L’argument de type doit être un type valeur (ajoutez la contrainte `Structure` )</span><span class="sxs-lookup"><span data-stu-id="b2654-110">The type argument must be a value type (include the `Structure` constraint)</span></span>  
  
- <span data-ttu-id="b2654-111">L’argument de type doit être un type référence (ajoutez la contrainte `Class` )</span><span class="sxs-lookup"><span data-stu-id="b2654-111">The type argument must be a reference type (include the `Class` constraint)</span></span>  
  
 <span data-ttu-id="b2654-112">Vous ne pouvez pas spécifier à la fois `Structure` et `Class` pour le même paramètre de type et vous ne pouvez pas spécifier l’une des deux plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="b2654-112">You cannot specify both `Structure` and `Class` for the same type parameter, and you cannot specify either one more than once.</span></span>  
  
 <span data-ttu-id="b2654-113">**ID d’erreur :** BC32061</span><span class="sxs-lookup"><span data-stu-id="b2654-113">**Error ID:** BC32061</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b2654-114">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="b2654-114">To correct this error</span></span>  
  
- <span data-ttu-id="b2654-115">Vérifiez que l’expression et ses éléments sont correctement orthographiés.</span><span class="sxs-lookup"><span data-stu-id="b2654-115">Verify that the expression and its elements are spelled correctly.</span></span>  
  
- <span data-ttu-id="b2654-116">Si l’expression ne répond pas à la précédente liste d’exigences, supprimez-la de la liste des contraintes.</span><span class="sxs-lookup"><span data-stu-id="b2654-116">If the expression does not qualify for the preceding list of requirements, remove it from the constraint list.</span></span>  
  
- <span data-ttu-id="b2654-117">Si l’expression fait référence à une interface ou une classe, vérifiez que le compilateur a accès à cette interface ou classe.</span><span class="sxs-lookup"><span data-stu-id="b2654-117">If the expression refers to an interface or class, verify that the compiler has access to that interface or class.</span></span> <span data-ttu-id="b2654-118">Vous devrez peut-être qualifier son nom et ajouter une référence à votre projet.</span><span class="sxs-lookup"><span data-stu-id="b2654-118">You might need to qualify its name, and you might need to add a reference to your project.</span></span> <span data-ttu-id="b2654-119">Pour plus d’informations, consultez « références aux projets » dans les [références aux éléments déclarés](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="b2654-119">For more information, see "References to Projects" in [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2654-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b2654-120">See also</span></span>

- [<span data-ttu-id="b2654-121">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b2654-121">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="b2654-122">Types valeur et types référence</span><span class="sxs-lookup"><span data-stu-id="b2654-122">Value Types and Reference Types</span></span>](../../programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="b2654-123">References to Declared Elements</span><span class="sxs-lookup"><span data-stu-id="b2654-123">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
