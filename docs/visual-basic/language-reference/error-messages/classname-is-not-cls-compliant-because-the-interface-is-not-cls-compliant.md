---
title: "'<classname>' n'est pas conforme CLS, car l'interface '<interfacename>' qu'il implémente n'est pas conforme CLS"
ms.date: 07/20/2015
f1_keywords:
- bc40029
- vbc40029
helpviewer_keywords:
- BC40029
ms.assetid: 178452f3-5575-4da0-9d6c-53bcddb6a338
ms.openlocfilehash: a482d14094a3fa86b56ca84af46c45e6093416c5
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874625"
---
# <a name="classname-is-not-cls-compliant-because-the-interface-interfacename-it-implements-is-not-cls-compliant"></a><span data-ttu-id="5fd1c-102">'\<classname>' n'est pas conforme CLS, car l'interface '\<interfacename>' qu'il implémente n'est pas conforme CLS</span><span class="sxs-lookup"><span data-stu-id="5fd1c-102">'\<classname>' is not CLS-compliant because the interface '\<interfacename>' it implements is not CLS-compliant</span></span>

<span data-ttu-id="5fd1c-103">Une classe ou une interface est marquée comme `<CLSCompliant(True)>` quand elle est dérivée d’un type ou implémente un type qui est marqué comme `<CLSCompliant(False)>` ou qui n’est pas marqué.</span><span class="sxs-lookup"><span data-stu-id="5fd1c-103">A class or interface is marked as `<CLSCompliant(True)>` when it derives from or implements a type that is marked as `<CLSCompliant(False)>` or is not marked.</span></span>  
  
 <span data-ttu-id="5fd1c-104">Pour qu’une classe ou une interface soit conforme à l' [indépendance du langage et aux composants indépendants du langage (CLS, Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) ), toute la hiérarchie d’héritage doit être conforme.</span><span class="sxs-lookup"><span data-stu-id="5fd1c-104">For a class or interface to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), its entire inheritance hierarchy must be compliant.</span></span> <span data-ttu-id="5fd1c-105">Cela signifie que chaque type dont elle hérite, directement ou indirectement, doit être conforme.</span><span class="sxs-lookup"><span data-stu-id="5fd1c-105">That means every type from which it inherits, directly or indirectly, must be compliant.</span></span> <span data-ttu-id="5fd1c-106">De même, si une classe implémente une ou plusieurs interfaces, celles-ci doivent toutes être conformes au sein de leurs hiérarchies d’héritage.</span><span class="sxs-lookup"><span data-stu-id="5fd1c-106">Similarly, if a class implements one or more interfaces, they must all be compliant throughout their inheritance hierarchies.</span></span>  
  
 <span data-ttu-id="5fd1c-107">Quand vous appliquez l’attribut <xref:System.CLSCompliantAttribute> à un élément de programmation, vous affectez au paramètre `isCompliant` de l’attribut la valeur `True` ou `False` pour indiquer la conformité ou la non-conformité.</span><span class="sxs-lookup"><span data-stu-id="5fd1c-107">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="5fd1c-108">Il n’existe pas de valeur par défaut pour ce paramètre et vous devez fournir une valeur.</span><span class="sxs-lookup"><span data-stu-id="5fd1c-108">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="5fd1c-109">Si vous n’appliquez pas <xref:System.CLSCompliantAttribute> à un élément, il est considéré comme étant non conforme.</span><span class="sxs-lookup"><span data-stu-id="5fd1c-109">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="5fd1c-110">Par défaut, ce message est un avertissement.</span><span class="sxs-lookup"><span data-stu-id="5fd1c-110">By default, this message is a warning.</span></span> <span data-ttu-id="5fd1c-111">Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="5fd1c-111">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="5fd1c-112">**ID d’erreur :** BC40029</span><span class="sxs-lookup"><span data-stu-id="5fd1c-112">**Error ID:** BC40029</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5fd1c-113">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="5fd1c-113">To correct this error</span></span>  
  
- <span data-ttu-id="5fd1c-114">Si la conformité CLS est obligatoire, définissez ce type dans une autre hiérarchie d’héritage ou dans un autre schéma d’implémentation.</span><span class="sxs-lookup"><span data-stu-id="5fd1c-114">If you require CLS compliance, define this type within a different inheritance hierarchy or implementation scheme.</span></span>  
  
- <span data-ttu-id="5fd1c-115">Si le type doit rester au sein de sa hiérarchie d’héritage ou de son schéma d’implémentation actuels, supprimez <xref:System.CLSCompliantAttribute> de sa définition ou marquez-le comme `<CLSCompliant(False)>`.</span><span class="sxs-lookup"><span data-stu-id="5fd1c-115">If you require that this type remain within its current inheritance hierarchy or implementation scheme, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span>  
