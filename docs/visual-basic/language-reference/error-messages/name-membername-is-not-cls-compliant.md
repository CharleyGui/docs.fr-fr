---
title: Le nom <membername> n'est pas conforme CLS
ms.date: 07/20/2015
f1_keywords:
- bc40031
- vbc40031
helpviewer_keywords:
- BC40031
ms.assetid: e2b885dc-cbf9-49ff-bbbe-531657ea99f7
ms.openlocfilehash: 45c9332237dffc7311daeedaf36035d9e9958415
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397179"
---
# <a name="name-membername-is-not-cls-compliant"></a><span data-ttu-id="97671-102">Le nom \<membername> n'est pas conforme CLS</span><span class="sxs-lookup"><span data-stu-id="97671-102">Name \<membername> is not CLS-compliant</span></span>
<span data-ttu-id="97671-103">Un assembly est marqué comme, `<CLSCompliant(True)>` mais expose un membre avec un nom qui commence par un trait de soulignement ( `_` ).</span><span class="sxs-lookup"><span data-stu-id="97671-103">An assembly is marked as `<CLSCompliant(True)>` but exposes a member with a name that begins with an underscore (`_`).</span></span>  
  
 <span data-ttu-id="97671-104">Un élément de programmation peut contenir un ou plusieurs traits de soulignement, mais pour être conforme à l' [indépendance du langage et aux composants indépendants du langage](../../../standard/language-independence-and-language-independent-components.md) (CLS), il ne doit pas commencer par un trait de soulignement.</span><span class="sxs-lookup"><span data-stu-id="97671-104">A programming element can contain one or more underscores, but to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must not begin with an underscore.</span></span> <span data-ttu-id="97671-105">Consultez [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="97671-105">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 <span data-ttu-id="97671-106">Quand vous appliquez l’attribut <xref:System.CLSCompliantAttribute> à un élément de programmation, vous affectez au paramètre `isCompliant` de l’attribut la valeur `True` ou `False` pour indiquer la conformité ou la non-conformité.</span><span class="sxs-lookup"><span data-stu-id="97671-106">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="97671-107">Il n’existe pas de valeur par défaut pour ce paramètre et vous devez fournir une valeur.</span><span class="sxs-lookup"><span data-stu-id="97671-107">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="97671-108">Si vous n’appliquez pas <xref:System.CLSCompliantAttribute> à un élément, il est considéré comme étant non conforme.</span><span class="sxs-lookup"><span data-stu-id="97671-108">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="97671-109">Par défaut, ce message est un avertissement.</span><span class="sxs-lookup"><span data-stu-id="97671-109">By default, this message is a warning.</span></span> <span data-ttu-id="97671-110">Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="97671-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="97671-111">**ID d’erreur :** BC40031</span><span class="sxs-lookup"><span data-stu-id="97671-111">**Error ID:** BC40031</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="97671-112">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="97671-112">To correct this error</span></span>  
  
- <span data-ttu-id="97671-113">Si vous contrôlez le code source, modifiez le nom du membre afin qu’il ne commence pas par un trait de soulignement.</span><span class="sxs-lookup"><span data-stu-id="97671-113">If you have control over the source code, change the member name so that it does not begin with an underscore.</span></span>  
  
- <span data-ttu-id="97671-114">Si vous avez besoin que le nom du membre reste inchangé, supprimez <xref:System.CLSCompliantAttribute> de sa définition ou marquez-le comme `<CLSCompliant(False)>` .</span><span class="sxs-lookup"><span data-stu-id="97671-114">If you require that the member name remain unchanged, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span> <span data-ttu-id="97671-115">Vous pouvez toujours marquer l’assembly comme `<CLSCompliant(True)>` .</span><span class="sxs-lookup"><span data-stu-id="97671-115">You can still mark the assembly as `<CLSCompliant(True)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97671-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="97671-116">See also</span></span>

- [<span data-ttu-id="97671-117">Declared Element Names</span><span class="sxs-lookup"><span data-stu-id="97671-117">Declared Element Names</span></span>](../../programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="97671-118">Conventions d'affectation de noms Visual Basic</span><span class="sxs-lookup"><span data-stu-id="97671-118">Visual Basic Naming Conventions</span></span>](../../programming-guide/program-structure/naming-conventions.md)
