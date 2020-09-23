---
title: Promotion de type
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- Partial keyword [Visual Basic], unexpected results with type promotion
- scope [Visual Basic], declared elements
- scope [Visual Basic], Visual Basic
- type promotion
- declared elements [Visual Basic], visibility
ms.assetid: 035eeb15-e4c5-4288-ab3c-6bd5d22f7051
ms.openlocfilehash: 6c28ca22e96616ff09e147400bfdb2adb922ff0e
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085800"
---
# <a name="type-promotion-visual-basic"></a><span data-ttu-id="4056b-102">Promotion de type (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4056b-102">Type Promotion (Visual Basic)</span></span>

<span data-ttu-id="4056b-103">Quand vous déclarez un élément de programmation dans un module, Visual Basic promeut son étendue vers l’espace de noms contenant le module.</span><span class="sxs-lookup"><span data-stu-id="4056b-103">When you declare a programming element in a module, Visual Basic promotes its scope to the namespace containing the module.</span></span> <span data-ttu-id="4056b-104">C’est ce que l’on appelle la *promotion de type*.</span><span class="sxs-lookup"><span data-stu-id="4056b-104">This is known as *type promotion*.</span></span>  
  
 <span data-ttu-id="4056b-105">L’exemple suivant montre une définition squelette d’un module et de deux membres de ce module.</span><span class="sxs-lookup"><span data-stu-id="4056b-105">The following example shows a skeleton definition of a module and two members of that module.</span></span>  
  
 [!code-vb[VbVbalrDeclaredElements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#1)]  
  
 <span data-ttu-id="4056b-106">Dans `projModule` , les éléments de programmation déclarés au niveau du module sont promus en `projNamespace` .</span><span class="sxs-lookup"><span data-stu-id="4056b-106">Within `projModule`, programming elements declared at module level are promoted to `projNamespace`.</span></span> <span data-ttu-id="4056b-107">Dans l’exemple précédent, `basicEnum` et `innerClass` sont promus, mais `numberSub` n’est pas, car il n’est pas déclaré au niveau du module.</span><span class="sxs-lookup"><span data-stu-id="4056b-107">In the preceding example, `basicEnum` and `innerClass` are promoted, but `numberSub` is not, because it is not declared at module level.</span></span>  
  
## <a name="effect-of-type-promotion"></a><span data-ttu-id="4056b-108">Effet de la promotion de type</span><span class="sxs-lookup"><span data-stu-id="4056b-108">Effect of Type Promotion</span></span>  

 <span data-ttu-id="4056b-109">L’effet de la promotion de type est qu’une chaîne de qualification n’a pas besoin d’inclure le nom du module.</span><span class="sxs-lookup"><span data-stu-id="4056b-109">The effect of type promotion is that a qualification string does not need to include the module name.</span></span> <span data-ttu-id="4056b-110">L’exemple suivant effectue deux appels à la procédure dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="4056b-110">The following example makes two calls to the procedure in the preceding example.</span></span>  
  
 [!code-vb[VbVbalrDeclaredElements#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#2)]  
  
 <span data-ttu-id="4056b-111">Dans l’exemple précédent, le premier appel utilise des chaînes de qualification complètes.</span><span class="sxs-lookup"><span data-stu-id="4056b-111">In the preceding example, the first call uses complete qualification strings.</span></span> <span data-ttu-id="4056b-112">Toutefois, cela n’est pas nécessaire en raison de la promotion de type.</span><span class="sxs-lookup"><span data-stu-id="4056b-112">However, this is not necessary because of type promotion.</span></span> <span data-ttu-id="4056b-113">Le deuxième appel accède également aux membres du module sans inclure `projModule` dans les chaînes de qualification.</span><span class="sxs-lookup"><span data-stu-id="4056b-113">The second call also accesses the module's members without including `projModule` in the qualification strings.</span></span>  
  
## <a name="defeat-of-type-promotion"></a><span data-ttu-id="4056b-114">Invalidation de la promotion de type</span><span class="sxs-lookup"><span data-stu-id="4056b-114">Defeat of Type Promotion</span></span>  

 <span data-ttu-id="4056b-115">Si l’espace de noms a déjà un membre portant le même nom qu’un membre de module, la promotion de type est invalidée pour ce membre de module.</span><span class="sxs-lookup"><span data-stu-id="4056b-115">If the namespace already has a member with the same name as a module member, type promotion is defeated for that module member.</span></span> <span data-ttu-id="4056b-116">L’exemple suivant montre une définition squelette d’une énumération et d’un module au sein du même espace de noms.</span><span class="sxs-lookup"><span data-stu-id="4056b-116">The following example shows a skeleton definition of an enumeration and a module within the same namespace.</span></span>  
  
 [!code-vb[VbVbalrDeclaredElements#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#3)]  
  
 <span data-ttu-id="4056b-117">Dans l’exemple précédent, Visual Basic ne peut pas `abc` promouvoir `thisNameSpace` la classe vers, car il existe déjà une énumération portant le même nom au niveau de l’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="4056b-117">In the preceding example, Visual Basic cannot promote class `abc` to `thisNameSpace` because there is already an enumeration with the same name at namespace level.</span></span> <span data-ttu-id="4056b-118">Pour accéder à `abcSub` , vous devez utiliser la chaîne de qualification complète `thisNamespace.thisModule.abc.abcSub` .</span><span class="sxs-lookup"><span data-stu-id="4056b-118">To access `abcSub`, you must use the full qualification string `thisNamespace.thisModule.abc.abcSub`.</span></span> <span data-ttu-id="4056b-119">Toutefois, `xyz` la classe est toujours promue et vous pouvez y accéder `xyzSub` avec la chaîne de qualification plus petite `thisNamespace.xyz.xyzSub` .</span><span class="sxs-lookup"><span data-stu-id="4056b-119">However, class `xyz` is still promoted, and you can access `xyzSub` with the shorter qualification string `thisNamespace.xyz.xyzSub`.</span></span>  
  
### <a name="defeat-of-type-promotion-for-partial-types"></a><span data-ttu-id="4056b-120">Non-manipulation de la promotion de type pour les types partiels</span><span class="sxs-lookup"><span data-stu-id="4056b-120">Defeat of Type Promotion for Partial Types</span></span>  

 <span data-ttu-id="4056b-121">Si une classe ou une structure à l’intérieur d’un module utilise le mot clé [Partial](../../../language-reference/modifiers/partial.md) , la promotion de type est automatiquement invalidée pour cette classe ou structure, que l’espace de noms ait ou non un membre avec le même nom.</span><span class="sxs-lookup"><span data-stu-id="4056b-121">If a class or structure inside a module uses the [Partial](../../../language-reference/modifiers/partial.md) keyword, type promotion is automatically defeated for that class or structure, whether or not the namespace has a member with the same name.</span></span> <span data-ttu-id="4056b-122">D’autres éléments du module sont toujours éligibles pour la promotion de type.</span><span class="sxs-lookup"><span data-stu-id="4056b-122">Other elements in the module are still eligible for type promotion.</span></span>  
  
 <span data-ttu-id="4056b-123">**Incidences.**</span><span class="sxs-lookup"><span data-stu-id="4056b-123">**Consequences.**</span></span> <span data-ttu-id="4056b-124">L’invalidation de la promotion de type d’une définition partielle peut provoquer des résultats inattendus et même des erreurs du compilateur.</span><span class="sxs-lookup"><span data-stu-id="4056b-124">Defeat of type promotion of a partial definition can cause unexpected results and even compiler errors.</span></span> <span data-ttu-id="4056b-125">L’exemple suivant illustre le squelette des définitions partielles d’une classe, dont l’une est à l’intérieur d’un module.</span><span class="sxs-lookup"><span data-stu-id="4056b-125">The following example shows skeleton partial definitions of a class, one of which is inside a module.</span></span>  
  
 [!code-vb[VbVbalrDeclaredElements#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#4)]  
  
 <span data-ttu-id="4056b-126">Dans l’exemple précédent, le développeur peut s’attendre à ce que le compilateur fusionne les deux définitions partielles de `sampleClass` .</span><span class="sxs-lookup"><span data-stu-id="4056b-126">In the preceding example, the developer might expect the compiler to merge the two partial definitions of `sampleClass`.</span></span> <span data-ttu-id="4056b-127">Toutefois, le compilateur ne tient pas compte de la promotion pour la définition partielle à l’intérieur de `sampleModule` .</span><span class="sxs-lookup"><span data-stu-id="4056b-127">However, the compiler does not consider promotion for the partial definition inside `sampleModule`.</span></span> <span data-ttu-id="4056b-128">Par conséquent, il tente de compiler deux classes distinctes et distinctes, à la fois nommées, `sampleClass` mais avec des chemins de qualification différents.</span><span class="sxs-lookup"><span data-stu-id="4056b-128">As a result, it attempts to compile two separate and distinct classes, both named `sampleClass` but with different qualification paths.</span></span>  
  
 <span data-ttu-id="4056b-129">Le compilateur fusionne des définitions partielles uniquement lorsque leurs chemins qualifiés complets sont identiques.</span><span class="sxs-lookup"><span data-stu-id="4056b-129">The compiler merges partial definitions only when their fully qualified paths are identical.</span></span>  
  
## <a name="recommendations"></a><span data-ttu-id="4056b-130">Recommandations</span><span class="sxs-lookup"><span data-stu-id="4056b-130">Recommendations</span></span>  

 <span data-ttu-id="4056b-131">Les recommandations suivantes représentent une bonne pratique de programmation.</span><span class="sxs-lookup"><span data-stu-id="4056b-131">The following recommendations represent good programming practice.</span></span>  
  
- <span data-ttu-id="4056b-132">**Noms uniques.**</span><span class="sxs-lookup"><span data-stu-id="4056b-132">**Unique Names.**</span></span> <span data-ttu-id="4056b-133">Lorsque vous avez un contrôle total sur le nom des éléments de programmation, il est toujours judicieux d’utiliser des noms uniques partout.</span><span class="sxs-lookup"><span data-stu-id="4056b-133">When you have full control over the naming of programming elements, it is always a good idea to use unique names everywhere.</span></span> <span data-ttu-id="4056b-134">Des noms identiques nécessitent une qualification supplémentaire et peuvent rendre votre code plus difficile à lire.</span><span class="sxs-lookup"><span data-stu-id="4056b-134">Identical names require extra qualification and can make your code harder to read.</span></span> <span data-ttu-id="4056b-135">Ils peuvent également entraîner des erreurs subtiles et des résultats inattendus.</span><span class="sxs-lookup"><span data-stu-id="4056b-135">They can also lead to subtle errors and unexpected results.</span></span>  
  
- <span data-ttu-id="4056b-136">**Qualification complète.**</span><span class="sxs-lookup"><span data-stu-id="4056b-136">**Full Qualification.**</span></span> <span data-ttu-id="4056b-137">Lorsque vous travaillez avec des modules et d’autres éléments dans le même espace de noms, l’approche la plus sûre consiste à toujours utiliser la qualification complète pour tous les éléments de programmation.</span><span class="sxs-lookup"><span data-stu-id="4056b-137">When you are working with modules and other elements in the same namespace, the safest approach is to always use full qualification for all programming elements.</span></span> <span data-ttu-id="4056b-138">Si la promotion de type est invalidée pour un membre de module et que vous ne qualifiez pas complètement ce membre, vous pouvez accéder par inadvertance à un élément de programmation différent.</span><span class="sxs-lookup"><span data-stu-id="4056b-138">If type promotion is defeated for a module member and you do not fully qualify that member, you could inadvertently access a different programming element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4056b-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4056b-139">See also</span></span>

- [<span data-ttu-id="4056b-140">Module, instruction</span><span class="sxs-lookup"><span data-stu-id="4056b-140">Module Statement</span></span>](../../../language-reference/statements/module-statement.md)
- [<span data-ttu-id="4056b-141">Namespace, instruction</span><span class="sxs-lookup"><span data-stu-id="4056b-141">Namespace Statement</span></span>](../../../language-reference/statements/namespace-statement.md)
- [<span data-ttu-id="4056b-142">Partial</span><span class="sxs-lookup"><span data-stu-id="4056b-142">Partial</span></span>](../../../language-reference/modifiers/partial.md)
- [<span data-ttu-id="4056b-143">Portée dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4056b-143">Scope in Visual Basic</span></span>](scope.md)
- [<span data-ttu-id="4056b-144">Comment : contrôler la portée d'une variable</span><span class="sxs-lookup"><span data-stu-id="4056b-144">How to: Control the Scope of a Variable</span></span>](how-to-control-the-scope-of-a-variable.md)
- [<span data-ttu-id="4056b-145">References to Declared Elements</span><span class="sxs-lookup"><span data-stu-id="4056b-145">References to Declared Elements</span></span>](references-to-declared-elements.md)
