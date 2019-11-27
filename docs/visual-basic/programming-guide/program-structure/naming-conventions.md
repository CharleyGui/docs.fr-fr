---
title: Conventions d'affectation des noms
ms.date: 07/20/2015
helpviewer_keywords:
- names [Visual Basic], Visual Basic rules
- naming conventions
- naming conventions [Visual Basic], Visual Basic
- Visual Basic code, naming conventions
- conventions [Visual Basic], Visual Basic coding
- names [Visual Basic], naming conventions
- naming conventions [Visual Basic], classes
ms.assetid: 164949a4-2a7c-4736-9d82-9c3078e2e56c
ms.openlocfilehash: 98fdda2934c9df1b33f41b6e0442a39246efe168
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347318"
---
# <a name="visual-basic-naming-conventions"></a><span data-ttu-id="2e169-102">Conventions d'affectation de noms Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2e169-102">Visual Basic Naming Conventions</span></span>
<span data-ttu-id="2e169-103">Lorsque vous nommez un élément dans votre application Visual Basic, le premier caractère de ce nom doit être un caractère alphabétique ou un trait de soulignement.</span><span class="sxs-lookup"><span data-stu-id="2e169-103">When you name an element in your Visual Basic application, the first character of that name must be an alphabetic character or an underscore.</span></span> <span data-ttu-id="2e169-104">Notez, toutefois, que les noms commençant par un trait de soulignement ne sont pas conformes à l' [indépendance du langage et aux composants indépendants du langage](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span><span class="sxs-lookup"><span data-stu-id="2e169-104">Note, however, that names beginning with an underscore are not compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span>  
  
 <span data-ttu-id="2e169-105">Les suggestions suivantes s’appliquent à l’affectation de noms.</span><span class="sxs-lookup"><span data-stu-id="2e169-105">The following suggestions apply to naming.</span></span>  
  
- <span data-ttu-id="2e169-106">Commencez chaque mot distinct d’un nom par une lettre majuscule, comme dans `FindLastRecord` et `RedrawMyForm`.</span><span class="sxs-lookup"><span data-stu-id="2e169-106">Begin each separate word in a name with a capital letter, as in `FindLastRecord` and `RedrawMyForm`.</span></span>  
  
- <span data-ttu-id="2e169-107">Commencer les noms de fonction et de méthode par un verbe, comme dans `InitNameArray` ou `CloseDialog`.</span><span class="sxs-lookup"><span data-stu-id="2e169-107">Begin function and method names with a verb, as in `InitNameArray` or `CloseDialog`.</span></span>  
  
- <span data-ttu-id="2e169-108">Commencez les noms de classe, de structure, de module et de propriété par un nom, comme dans `EmployeeName` ou `CarAccessory`.</span><span class="sxs-lookup"><span data-stu-id="2e169-108">Begin class, structure, module, and property names with a noun, as in `EmployeeName` or `CarAccessory`.</span></span>  
  
- <span data-ttu-id="2e169-109">Commencez les noms d’interface par le préfixe « I », suivi d’un nom ou d’une expression nominale, comme `IComponent`ou avec un adjectif décrivant le comportement de l’interface, comme `IPersistable`.</span><span class="sxs-lookup"><span data-stu-id="2e169-109">Begin interface names with the prefix "I", followed by a noun or a noun phrase, like `IComponent`, or with an adjective describing the interface's behavior, like `IPersistable`.</span></span> <span data-ttu-id="2e169-110">N’utilisez pas de trait de soulignement et utilisez des abréviations avec modération, car les abréviations peuvent entraîner des confusions.</span><span class="sxs-lookup"><span data-stu-id="2e169-110">Do not use the underscore, and use abbreviations sparingly, because abbreviations can cause confusion.</span></span>  
  
- <span data-ttu-id="2e169-111">Commencez les noms de gestionnaires d’événements par un nom décrivant le type d’événement suivi du suffixe «`EventHandler`», comme dans «`MouseEventHandler`».</span><span class="sxs-lookup"><span data-stu-id="2e169-111">Begin event handler names with a noun describing the type of event followed by the "`EventHandler`" suffix, as in "`MouseEventHandler`".</span></span>  
  
- <span data-ttu-id="2e169-112">Dans noms des classes d’arguments d’événement, incluez le suffixe «`EventArgs`».</span><span class="sxs-lookup"><span data-stu-id="2e169-112">In names of event argument classes, include the "`EventArgs`" suffix.</span></span>  
  
- <span data-ttu-id="2e169-113">Si un événement a le concept « Before » ou « after », utilisez un suffixe dans le présent ou le passé, comme dans «`ControlAdd`» ou «`ControlAdded`».</span><span class="sxs-lookup"><span data-stu-id="2e169-113">If an event has a concept of "before" or "after," use a suffix in present or past tense, as in "`ControlAdd`" or "`ControlAdded`".</span></span>  
  
- <span data-ttu-id="2e169-114">Pour les termes longs ou fréquemment utilisés, utilisez des abréviations pour conserver les longueurs de noms raisonnables, par exemple, « HTML », au lieu de « langage HTML ».</span><span class="sxs-lookup"><span data-stu-id="2e169-114">For long or frequently used terms, use abbreviations to keep name lengths reasonable, for example, "HTML", instead of "Hypertext Markup Language".</span></span> <span data-ttu-id="2e169-115">En général, les noms de variables de plus de 32 caractères sont difficiles à lire sur une analyse définie sur une résolution faible.</span><span class="sxs-lookup"><span data-stu-id="2e169-115">In general, variable names greater than 32 characters are difficult to read on a monitor set to a low resolution.</span></span> <span data-ttu-id="2e169-116">En outre, assurez-vous que vos abréviations sont cohérentes dans toute l’application.</span><span class="sxs-lookup"><span data-stu-id="2e169-116">Also, make sure your abbreviations are consistent throughout the entire application.</span></span> <span data-ttu-id="2e169-117">Le basculement aléatoire d’un projet entre « HTML » et « langage HTML » peut entraîner des confusions.</span><span class="sxs-lookup"><span data-stu-id="2e169-117">Randomly switching in a project between "HTML" and "Hypertext Markup Language" can lead to confusion.</span></span>  
  
- <span data-ttu-id="2e169-118">Évitez d’utiliser des noms dans une portée interne qui sont identiques aux noms dans une portée externe.</span><span class="sxs-lookup"><span data-stu-id="2e169-118">Avoid using names in an inner scope that are the same as names in an outer scope.</span></span> <span data-ttu-id="2e169-119">Des erreurs peuvent se produire en cas d’accès à la mauvaise variable.</span><span class="sxs-lookup"><span data-stu-id="2e169-119">Errors can result if the wrong variable is accessed.</span></span> <span data-ttu-id="2e169-120">Si un conflit se produit entre une variable et le mot clé du même nom, vous devez identifier le mot clé en le faisant précéder de la bibliothèque de types appropriée.</span><span class="sxs-lookup"><span data-stu-id="2e169-120">If a conflict occurs between a variable and the keyword of the same name, you must identify the keyword by preceding it with the appropriate type library.</span></span> <span data-ttu-id="2e169-121">Par exemple, si vous avez une variable appelée `Date`, vous pouvez utiliser la fonction `Date` intrinsèque uniquement en appelant <xref:System.DateTime.Date%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2e169-121">For example, if you have a variable called `Date`, you can use the intrinsic `Date` function only by calling <xref:System.DateTime.Date%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e169-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2e169-122">See also</span></span>

- [<span data-ttu-id="2e169-123">Utilisation des mots clés comme noms d’éléments dans le code</span><span class="sxs-lookup"><span data-stu-id="2e169-123">Keywords as Element Names in Code</span></span>](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)
- [<span data-ttu-id="2e169-124">Me, My, MyBase et MyClass</span><span class="sxs-lookup"><span data-stu-id="2e169-124">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="2e169-125">Noms d’éléments déclarés</span><span class="sxs-lookup"><span data-stu-id="2e169-125">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="2e169-126">Structure de programme et conventions de codage</span><span class="sxs-lookup"><span data-stu-id="2e169-126">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [<span data-ttu-id="2e169-127">Informations de référence sur le langage Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2e169-127">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)
