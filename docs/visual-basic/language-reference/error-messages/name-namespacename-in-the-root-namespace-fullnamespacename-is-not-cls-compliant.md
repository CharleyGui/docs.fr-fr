---
title: Le nom <namespacename> de l'espace de noms racine <fullnamespacename> n'est pas conforme CLS
ms.date: 07/20/2015
f1_keywords:
- vbc40039
- bc40039
helpviewer_keywords:
- BC40039
ms.assetid: c5bd5914-ae71-416a-8bed-f76f644f78be
ms.openlocfilehash: 821044d3ee359a052fa6a763e9c5a89da5d6f607
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775579"
---
# <a name="name-namespacename-in-the-root-namespace-fullnamespacename-is-not-cls-compliant"></a><span data-ttu-id="bd158-102">Nom \<namespacename > dans l’espace de noms racine \<fullnamespacename > n’est pas conforme CLS</span><span class="sxs-lookup"><span data-stu-id="bd158-102">Name \<namespacename> in the root namespace \<fullnamespacename> is not CLS-compliant</span></span>
<span data-ttu-id="bd158-103">Un assembly est marqué comme `<CLSCompliant(True)>`, mais un élément du nom de l’espace de noms racine commence par un trait de soulignement (`_`).</span><span class="sxs-lookup"><span data-stu-id="bd158-103">An assembly is marked as `<CLSCompliant(True)>`, but an element of the root namespace name begins with an underscore (`_`).</span></span>  
  
 <span data-ttu-id="bd158-104">Un élément de programmation peut contenir un ou plusieurs traits de soulignement, mais pour être conforme à l' [indépendance du langage et aux composants indépendants du langage](../../../standard/language-independence-and-language-independent-components.md) (CLS), il ne doit pas commencer par un trait de soulignement.</span><span class="sxs-lookup"><span data-stu-id="bd158-104">A programming element can contain one or more underscores, but to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must not begin with an underscore.</span></span> <span data-ttu-id="bd158-105">Consultez [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="bd158-105">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 <span data-ttu-id="bd158-106">Quand vous appliquez l’attribut <xref:System.CLSCompliantAttribute> à un élément de programmation, vous affectez au paramètre `isCompliant` de l’attribut la valeur `True` ou `False` pour indiquer la conformité ou la non-conformité.</span><span class="sxs-lookup"><span data-stu-id="bd158-106">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="bd158-107">Il n’existe pas de valeur par défaut pour ce paramètre et vous devez fournir une valeur.</span><span class="sxs-lookup"><span data-stu-id="bd158-107">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="bd158-108">Si vous n’appliquez pas <xref:System.CLSCompliantAttribute> à un élément, il est considéré comme étant non conforme.</span><span class="sxs-lookup"><span data-stu-id="bd158-108">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="bd158-109">Par défaut, ce message est un avertissement.</span><span class="sxs-lookup"><span data-stu-id="bd158-109">By default, this message is a warning.</span></span> <span data-ttu-id="bd158-110">Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="bd158-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="bd158-111">**ID d’erreur :** BC40039</span><span class="sxs-lookup"><span data-stu-id="bd158-111">**Error ID:** BC40039</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bd158-112">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="bd158-112">To correct this error</span></span>  
  
- <span data-ttu-id="bd158-113">Si la conformité CLS est nécessaire, modifiez le nom de l’espace de noms racine afin qu’aucun de ses éléments ne commence par un trait de soulignement.</span><span class="sxs-lookup"><span data-stu-id="bd158-113">If you require CLS compliance, change the root namespace name so that none of its elements begins with an underscore.</span></span>  
  
- <span data-ttu-id="bd158-114">Si vous avez besoin que le nom de l’espace de noms reste inchangé, supprimez le <xref:System.CLSCompliantAttribute> de l’assembly ou marquez-le comme `<CLSCompliant(False)>`.</span><span class="sxs-lookup"><span data-stu-id="bd158-114">If you require that the namespace name remain unchanged, then remove the <xref:System.CLSCompliantAttribute> from the assembly or mark it as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd158-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bd158-115">See also</span></span>

- [<span data-ttu-id="bd158-116">Namespace (instruction)</span><span class="sxs-lookup"><span data-stu-id="bd158-116">Namespace Statement</span></span>](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [<span data-ttu-id="bd158-117">Espaces de noms dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bd158-117">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="bd158-118">-rootnamespace</span><span class="sxs-lookup"><span data-stu-id="bd158-118">-rootnamespace</span></span>](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)
- [<span data-ttu-id="bd158-119">Page Application, Concepteur de projet (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bd158-119">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [<span data-ttu-id="bd158-120">Noms d’éléments déclarés</span><span class="sxs-lookup"><span data-stu-id="bd158-120">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="bd158-121">Conventions d’affectation de noms Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bd158-121">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
