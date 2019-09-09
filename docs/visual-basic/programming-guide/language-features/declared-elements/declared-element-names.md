---
title: Noms d'éléments déclarés (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic], case sensitivity
- names [Visual Basic], Visual Basic rules
- naming conventions [Visual Basic]
- element names [Visual Basic]
- declared elements [Visual Basic], identifiers
- declarations [Visual Basic], elements
- declared elements [Visual Basic], valid names
- '[] escape characters [Visual Basic]'
- names [Visual Basic], elements
- declaration statements [Visual Basic], declared elements
- declaring elements [Visual Basic]
- identifiers [Visual Basic], declared elements
- case sensitivity, declared element names
- escape characters [Visual Basic]
- names [Visual Basic], declared elements
- declared elements [Visual Basic], about declared elements
- escaped names [Visual Basic]
- declared elements [Visual Basic], names
- names [Visual Basic], naming conventions
- identifiers [Visual Basic], elements
ms.assetid: 09d8843b-c0dc-4afe-9dab-87c439a69e66
ms.openlocfilehash: 8a1b4869588c8dd030cf6276969063ec99b79e33
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046583"
---
# <a name="declared-element-names-visual-basic"></a><span data-ttu-id="a3c90-102">Noms d'éléments déclarés (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a3c90-102">Declared Element Names (Visual Basic)</span></span>
<span data-ttu-id="a3c90-103">Chaque élément déclaré a un nom, également appelé *identificateur*, qui est utilisé par le code pour y faire référence.</span><span class="sxs-lookup"><span data-stu-id="a3c90-103">Every declared element has a name, also called an *identifier*, which is what the code uses to refer to it.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="a3c90-104">Règles</span><span class="sxs-lookup"><span data-stu-id="a3c90-104">Rules</span></span>  
 <span data-ttu-id="a3c90-105">Un nom d’élément dans Visual Basic doit respecter les règles suivantes :</span><span class="sxs-lookup"><span data-stu-id="a3c90-105">An element name in Visual Basic must observe the following rules:</span></span>  
  
- <span data-ttu-id="a3c90-106">Elle doit commencer par un caractère alphabétique ou un trait de soulignement (`_`).</span><span class="sxs-lookup"><span data-stu-id="a3c90-106">It must begin with an alphabetic character or an underscore (`_`).</span></span>  
  
- <span data-ttu-id="a3c90-107">Il doit contenir uniquement des caractères alphabétiques, des chiffres décimaux et des traits de soulignement.</span><span class="sxs-lookup"><span data-stu-id="a3c90-107">It must only contain alphabetic characters, decimal digits, and underscores.</span></span>  
  
- <span data-ttu-id="a3c90-108">Il doit contenir au moins un caractère alphabétique ou un chiffre décimal s’il commence par un trait de soulignement.</span><span class="sxs-lookup"><span data-stu-id="a3c90-108">It must contain at least one alphabetic character or decimal digit if it begins with an underscore.</span></span>  
  
- <span data-ttu-id="a3c90-109">Sa longueur ne doit pas dépasser 1023 caractères.</span><span class="sxs-lookup"><span data-stu-id="a3c90-109">It must not be more than 1023 characters long.</span></span>  
  
 <span data-ttu-id="a3c90-110">La limite de longueur de 1023 caractères s’applique également à la chaîne entière d’un nom qualifié complet, `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`par exemple.</span><span class="sxs-lookup"><span data-stu-id="a3c90-110">The length limit of 1023 characters also applies to the entire string of a fully qualified name, such as `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`.</span></span>  
  
 <span data-ttu-id="a3c90-111">L’exemple suivant montre des noms d’éléments valides.</span><span class="sxs-lookup"><span data-stu-id="a3c90-111">The following example shows some valid element names.</span></span>  
  
 `aB123__45`  
  
 `_567`  
  
 <span data-ttu-id="a3c90-112">L’exemple suivant montre des noms d’éléments non valides.</span><span class="sxs-lookup"><span data-stu-id="a3c90-112">The following example shows some invalid element names.</span></span> <span data-ttu-id="a3c90-113">Le premier contient uniquement un trait de soulignement, le deuxième commence par un chiffre décimal et le troisième contient un caractère non valide ($).</span><span class="sxs-lookup"><span data-stu-id="a3c90-113">The first contains only an underscore, the second begins with a decimal digit, and the third contains an invalid character ($).</span></span>  
  
 `' Three INVALID element names`  
  
 `_`  
  
 `12ABC`  
  
 `xyz$wv`  
  
> [!CAUTION]
> <span data-ttu-id="a3c90-114">Les noms d’éléments commençant par un trait`_`de soulignement () ne font pas partie de l' [indépendance du langage et des composants indépendants du langage](../../../../standard/language-independence-and-language-independent-components.md) (CLS), de sorte que le code conforme CLS ne peut pas utiliser un composant qui définit ces noms.</span><span class="sxs-lookup"><span data-stu-id="a3c90-114">Element names starting with an underscore (`_`) are not part of the [Language Independence and Language-Independent Components](../../../../standard/language-independence-and-language-independent-components.md) (CLS), so CLS-compliant code cannot use a component that defines such names.</span></span> <span data-ttu-id="a3c90-115">Toutefois, un trait de soulignement à toute autre position dans un nom d’élément est conforme CLS.</span><span class="sxs-lookup"><span data-stu-id="a3c90-115">However, an underscore in any other position in an element name is CLS-compliant.</span></span>  
  
### <a name="name-length-guidelines"></a><span data-ttu-id="a3c90-116">Instructions relatives à la longueur de nom</span><span class="sxs-lookup"><span data-stu-id="a3c90-116">Name Length Guidelines</span></span>  
 <span data-ttu-id="a3c90-117">En pratique, votre nom doit être le plus bref possible tout en identifiant clairement la nature de l’élément.</span><span class="sxs-lookup"><span data-stu-id="a3c90-117">As a practical matter, your name should be as short as possible while still clearly identifying the nature of the element.</span></span> <span data-ttu-id="a3c90-118">Cela permet d’améliorer la lisibilité de votre code et de réduire la longueur de ligne et la taille du fichier source.</span><span class="sxs-lookup"><span data-stu-id="a3c90-118">This improves the readability of your code and reduces line length and source-file size.</span></span>  
  
 <span data-ttu-id="a3c90-119">En revanche, votre nom ne doit pas être tellement bref qu’il ne décrit pas correctement ce que l’élément représente et comment votre code l’utilise.</span><span class="sxs-lookup"><span data-stu-id="a3c90-119">On the other hand, your name should not be so short that it does not adequately describe what the element represents and how your code uses it.</span></span> <span data-ttu-id="a3c90-120">Cela est important pour la lisibilité de votre code.</span><span class="sxs-lookup"><span data-stu-id="a3c90-120">This is important for the readability of your code.</span></span> <span data-ttu-id="a3c90-121">Si quelqu’un d’autre essaie de le comprendre, ou si vous en examinez un peu plus longtemps après l’avoir écrit, les noms d’éléments appropriés peuvent gagner beaucoup de temps.</span><span class="sxs-lookup"><span data-stu-id="a3c90-121">If somebody else is trying to understand it, or if you yourself are looking at it a long time after you wrote it, suitable element names can save a considerable amount of time.</span></span>  
  
## <a name="escaped-names"></a><span data-ttu-id="a3c90-122">Noms placés dans une séquence d’échappement</span><span class="sxs-lookup"><span data-stu-id="a3c90-122">Escaped Names</span></span>  
 <span data-ttu-id="a3c90-123">En règle générale, un nom d’élément ne doit pas correspondre à un mot clé réservé par `Case` Visual Basic `Friend`, tel que ou.</span><span class="sxs-lookup"><span data-stu-id="a3c90-123">Generally, an element name must not match any of the keywords reserved by Visual Basic, such as `Case` or `Friend`.</span></span> <span data-ttu-id="a3c90-124">Toutefois, vous pouvez définir un *nom*placé dans une séquence d’échappement, placé entre`[ ]`crochets ().</span><span class="sxs-lookup"><span data-stu-id="a3c90-124">However, you can define an *escaped name*, which is enclosed by brackets (`[ ]`).</span></span> <span data-ttu-id="a3c90-125">Un nom échappé peut correspondre à n’importe quel mot clé Visual Basic, étant donné que les crochets suppriment toute ambiguïté.</span><span class="sxs-lookup"><span data-stu-id="a3c90-125">An escaped name can match any Visual Basic keyword, since the brackets remove any ambiguity.</span></span> <span data-ttu-id="a3c90-126">Vous utilisez également les crochets lorsque vous faites référence au nom plus loin dans votre code.</span><span class="sxs-lookup"><span data-stu-id="a3c90-126">You also use the brackets when you refer to the name later in your code.</span></span>  
  
 <span data-ttu-id="a3c90-127">En général, vous devez utiliser des noms échappés uniquement lorsque :</span><span class="sxs-lookup"><span data-stu-id="a3c90-127">In general, you should use escaped names only when:</span></span>  
  
- <span data-ttu-id="a3c90-128">Votre code a migré à partir d’une version antérieure de Visual Basic qui n’a pas réservé le mot clé utilisé comme nom ; ni</span><span class="sxs-lookup"><span data-stu-id="a3c90-128">Your code has migrated from a previous version of Visual Basic that did not reserve the keyword being used as a name; or</span></span>  
  
- <span data-ttu-id="a3c90-129">Vous travaillez avec du code écrit dans un autre langage dans lequel le mot clé donné n’est pas réservé.</span><span class="sxs-lookup"><span data-stu-id="a3c90-129">You are working with code written in another language in which the given keyword is not reserved.</span></span>  
  
 <span data-ttu-id="a3c90-130">Dans le cas contraire, vous devez envisager de renommer l’élément si son nom est en conflit avec un mot clé.</span><span class="sxs-lookup"><span data-stu-id="a3c90-130">Otherwise, you should consider renaming the element if its name conflicts with a keyword.</span></span> <span data-ttu-id="a3c90-131">L’environnement de développement intégré (IDE) offre un moyen simple de le faire.</span><span class="sxs-lookup"><span data-stu-id="a3c90-131">The integrated development environment (IDE) provides an easy way to do this.</span></span> <span data-ttu-id="a3c90-132">Pour plus d’informations, consultez [refactorisation](/visualstudio/vb-ide/refactoring-vb).</span><span class="sxs-lookup"><span data-stu-id="a3c90-132">For more information, see [Refactoring](/visualstudio/vb-ide/refactoring-vb).</span></span>  
  
## <a name="case-sensitivity-in-names"></a><span data-ttu-id="a3c90-133">Respect de la casse dans les noms</span><span class="sxs-lookup"><span data-stu-id="a3c90-133">Case Sensitivity in Names</span></span>  
 <span data-ttu-id="a3c90-134">Les noms d’éléments dans Visual Basic ne respectent pas la casse.</span><span class="sxs-lookup"><span data-stu-id="a3c90-134">Element names in Visual Basic are case-insensitive.</span></span> <span data-ttu-id="a3c90-135">Cela signifie que lorsque le compilateur compare deux noms qui diffèrent uniquement par la casse, il les interprète comme étant le même nom.</span><span class="sxs-lookup"><span data-stu-id="a3c90-135">This means that when the compiler compares two names that differ in alphabetic case only, it interprets them as the same name.</span></span> <span data-ttu-id="a3c90-136">Par exemple, il considère que `ABC` et `abc` font référence au même élément déclaré.</span><span class="sxs-lookup"><span data-stu-id="a3c90-136">For example, it considers `ABC` and `abc` to refer to the same declared element.</span></span>  
  
 <span data-ttu-id="a3c90-137">Toutefois, le common language runtime (CLR) utilise la liaison qui respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="a3c90-137">However, the common language runtime (CLR) uses case-sensitive binding.</span></span> <span data-ttu-id="a3c90-138">Ainsi, quand vous générez un assembly ou une DLL et que vous le mettez à disposition d’autres assemblys, la casse de vos noms est respectée.</span><span class="sxs-lookup"><span data-stu-id="a3c90-138">Therefore, when you produce an assembly or a DLL and make it available to other assemblies, your names are no longer case-insensitive.</span></span> <span data-ttu-id="a3c90-139">Par exemple, si vous définissez une classe avec un élément nommé `ABC`et que d’autres assemblys utilisent votre classe par le biais du Common Language Runtime, ils doivent faire référence à l’élément en tant que `ABC`.</span><span class="sxs-lookup"><span data-stu-id="a3c90-139">For example, if you define a class with an element called `ABC`, and other assemblies make use of your class through the common language runtime, they must refer to the element as `ABC`.</span></span> <span data-ttu-id="a3c90-140">Si, par la suite, vous recompilez votre classe et que `abc`vous changez le nom de l’élément en, les autres assemblys qui utilisent votre classe ne peuvent plus accéder à cet élément.</span><span class="sxs-lookup"><span data-stu-id="a3c90-140">If you subsequently recompile your class and change the element's name to `abc`, the other assemblies using your class could no longer access that element.</span></span> <span data-ttu-id="a3c90-141">Ainsi, quand vous publiez une version mise à jour d’un assembly, vous ne devez pas modifier la casse des éléments publics.</span><span class="sxs-lookup"><span data-stu-id="a3c90-141">Therefore, when you release an updated version of an assembly, you should not change the alphabetic case of any public elements.</span></span>  
  
## <a name="names-and-locales"></a><span data-ttu-id="a3c90-142">Noms et paramètres régionaux</span><span class="sxs-lookup"><span data-stu-id="a3c90-142">Names and Locales</span></span>  
 <span data-ttu-id="a3c90-143">Les comparaisons de noms sont indépendantes des paramètres régionaux.</span><span class="sxs-lookup"><span data-stu-id="a3c90-143">Comparison of names is independent of locale.</span></span> <span data-ttu-id="a3c90-144">Si deux noms correspondent à un paramètre régional, il est garanti qu’ils correspondent dans tous les paramètres régionaux.</span><span class="sxs-lookup"><span data-stu-id="a3c90-144">If two names match in one locale, they are guaranteed to match in all locales.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3c90-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a3c90-145">See also</span></span>

- [<span data-ttu-id="a3c90-146">Éléments déclarés</span><span class="sxs-lookup"><span data-stu-id="a3c90-146">Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)
- [<span data-ttu-id="a3c90-147">Caractéristiques d’éléments déclarés</span><span class="sxs-lookup"><span data-stu-id="a3c90-147">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [<span data-ttu-id="a3c90-148">Références aux éléments déclarés</span><span class="sxs-lookup"><span data-stu-id="a3c90-148">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="a3c90-149">Instructions</span><span class="sxs-lookup"><span data-stu-id="a3c90-149">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)
