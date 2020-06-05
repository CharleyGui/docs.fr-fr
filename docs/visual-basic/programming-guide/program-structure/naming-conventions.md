---
title: Conventions d'affectation de noms
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
ms.openlocfilehash: 20531e379ddf9b93a278795e9b3c0eb91b47e077
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398342"
---
# <a name="visual-basic-naming-conventions"></a><span data-ttu-id="58a79-102">Conventions d'affectation de noms Visual Basic</span><span class="sxs-lookup"><span data-stu-id="58a79-102">Visual Basic Naming Conventions</span></span>
<span data-ttu-id="58a79-103">Lorsque vous nommez un élément dans votre application Visual Basic, le premier caractère de ce nom doit être un caractère alphabétique ou un trait de soulignement.</span><span class="sxs-lookup"><span data-stu-id="58a79-103">When you name an element in your Visual Basic application, the first character of that name must be an alphabetic character or an underscore.</span></span> <span data-ttu-id="58a79-104">Notez, toutefois, que les noms commençant par un trait de soulignement ne sont pas conformes à l' [indépendance du langage et aux composants indépendants du langage](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span><span class="sxs-lookup"><span data-stu-id="58a79-104">Note, however, that names beginning with an underscore are not compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span>  
  
 <span data-ttu-id="58a79-105">Les suggestions suivantes s’appliquent à l’affectation de noms.</span><span class="sxs-lookup"><span data-stu-id="58a79-105">The following suggestions apply to naming.</span></span>  
  
- <span data-ttu-id="58a79-106">Commencez chaque mot distinct d’un nom par une lettre majuscule, comme dans `FindLastRecord` et `RedrawMyForm` .</span><span class="sxs-lookup"><span data-stu-id="58a79-106">Begin each separate word in a name with a capital letter, as in `FindLastRecord` and `RedrawMyForm`.</span></span>  
  
- <span data-ttu-id="58a79-107">Commencer les noms de fonction et de méthode par un verbe, comme dans `InitNameArray` ou `CloseDialog` .</span><span class="sxs-lookup"><span data-stu-id="58a79-107">Begin function and method names with a verb, as in `InitNameArray` or `CloseDialog`.</span></span>  
  
- <span data-ttu-id="58a79-108">Commencez les noms de classe, de structure, de module et de propriété par un nom, comme dans `EmployeeName` ou `CarAccessory` .</span><span class="sxs-lookup"><span data-stu-id="58a79-108">Begin class, structure, module, and property names with a noun, as in `EmployeeName` or `CarAccessory`.</span></span>  
  
- <span data-ttu-id="58a79-109">Commencez les noms d’interface par le préfixe « I », suivi d’un nom ou d’une expression nominale, comme `IComponent` , ou avec un adjectif décrivant le comportement de l’interface, par exemple `IPersistable` .</span><span class="sxs-lookup"><span data-stu-id="58a79-109">Begin interface names with the prefix "I", followed by a noun or a noun phrase, like `IComponent`, or with an adjective describing the interface's behavior, like `IPersistable`.</span></span> <span data-ttu-id="58a79-110">N’utilisez pas de trait de soulignement et utilisez des abréviations avec modération, car les abréviations peuvent entraîner des confusions.</span><span class="sxs-lookup"><span data-stu-id="58a79-110">Do not use the underscore, and use abbreviations sparingly, because abbreviations can cause confusion.</span></span>  
  
- <span data-ttu-id="58a79-111">Commencez les noms de gestionnaires d’événements par un nom décrivant le type d’événement suivi du `EventHandler` suffixe « », comme dans « `MouseEventHandler` ».</span><span class="sxs-lookup"><span data-stu-id="58a79-111">Begin event handler names with a noun describing the type of event followed by the "`EventHandler`" suffix, as in "`MouseEventHandler`".</span></span>  
  
- <span data-ttu-id="58a79-112">Dans les noms des classes d’arguments d’événement, incluez le `EventArgs` suffixe «».</span><span class="sxs-lookup"><span data-stu-id="58a79-112">In names of event argument classes, include the "`EventArgs`" suffix.</span></span>  
  
- <span data-ttu-id="58a79-113">Si un événement a le concept « Before » ou « after », utilisez un suffixe dans le présent ou le passé, comme dans « `ControlAdd` » ou « `ControlAdded` ».</span><span class="sxs-lookup"><span data-stu-id="58a79-113">If an event has a concept of "before" or "after," use a suffix in present or past tense, as in "`ControlAdd`" or "`ControlAdded`".</span></span>  
  
- <span data-ttu-id="58a79-114">Pour les termes longs ou fréquemment utilisés, utilisez des abréviations pour conserver les longueurs de noms raisonnables, par exemple, « HTML », au lieu de « langage HTML ».</span><span class="sxs-lookup"><span data-stu-id="58a79-114">For long or frequently used terms, use abbreviations to keep name lengths reasonable, for example, "HTML", instead of "Hypertext Markup Language".</span></span> <span data-ttu-id="58a79-115">En général, les noms de variables de plus de 32 caractères sont difficiles à lire sur une analyse définie sur une résolution faible.</span><span class="sxs-lookup"><span data-stu-id="58a79-115">In general, variable names greater than 32 characters are difficult to read on a monitor set to a low resolution.</span></span> <span data-ttu-id="58a79-116">En outre, assurez-vous que vos abréviations sont cohérentes dans toute l’application.</span><span class="sxs-lookup"><span data-stu-id="58a79-116">Also, make sure your abbreviations are consistent throughout the entire application.</span></span> <span data-ttu-id="58a79-117">Le basculement aléatoire d’un projet entre « HTML » et « langage HTML » peut entraîner des confusions.</span><span class="sxs-lookup"><span data-stu-id="58a79-117">Randomly switching in a project between "HTML" and "Hypertext Markup Language" can lead to confusion.</span></span>  
  
- <span data-ttu-id="58a79-118">Évitez d’utiliser des noms dans une portée interne qui sont identiques aux noms dans une portée externe.</span><span class="sxs-lookup"><span data-stu-id="58a79-118">Avoid using names in an inner scope that are the same as names in an outer scope.</span></span> <span data-ttu-id="58a79-119">Des erreurs peuvent se produire en cas d’accès à la mauvaise variable.</span><span class="sxs-lookup"><span data-stu-id="58a79-119">Errors can result if the wrong variable is accessed.</span></span> <span data-ttu-id="58a79-120">Si un conflit se produit entre une variable et le mot clé du même nom, vous devez identifier le mot clé en le faisant précéder de la bibliothèque de types appropriée.</span><span class="sxs-lookup"><span data-stu-id="58a79-120">If a conflict occurs between a variable and the keyword of the same name, you must identify the keyword by preceding it with the appropriate type library.</span></span> <span data-ttu-id="58a79-121">Par exemple, si vous avez une variable appelée `Date` , vous pouvez utiliser la `Date` fonction intrinsèque uniquement en appelant <xref:System.DateTime.Date%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="58a79-121">For example, if you have a variable called `Date`, you can use the intrinsic `Date` function only by calling <xref:System.DateTime.Date%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58a79-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="58a79-122">See also</span></span>

- [<span data-ttu-id="58a79-123">Mots clés comme noms d’éléments dans le code</span><span class="sxs-lookup"><span data-stu-id="58a79-123">Keywords as Element Names in Code</span></span>](keywords-as-element-names-in-code.md)
- [<span data-ttu-id="58a79-124">Me, My, MyBase et MyClass</span><span class="sxs-lookup"><span data-stu-id="58a79-124">Me, My, MyBase, and MyClass</span></span>](me-my-mybase-and-myclass.md)
- [<span data-ttu-id="58a79-125">Declared Element Names</span><span class="sxs-lookup"><span data-stu-id="58a79-125">Declared Element Names</span></span>](../language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="58a79-126">Structure de programme et conventions de code</span><span class="sxs-lookup"><span data-stu-id="58a79-126">Program Structure and Code Conventions</span></span>](program-structure-and-code-conventions.md)
- [<span data-ttu-id="58a79-127">Informations de référence sur le langage Visual Basic</span><span class="sxs-lookup"><span data-stu-id="58a79-127">Visual Basic Language Reference</span></span>](../../language-reference/index.md)
