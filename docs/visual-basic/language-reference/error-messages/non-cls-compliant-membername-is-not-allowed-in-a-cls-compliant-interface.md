---
title: Le <membername> non conforme CLS n'est pas autorisé dans une interface conforme CLS
ms.date: 07/20/2015
f1_keywords:
- bc40033
- vbc40033
helpviewer_keywords:
- BC40033
ms.assetid: 060c4b08-798e-40f1-94cf-c05c524f1b8a
ms.openlocfilehash: aa7944e90857436553435ce783c0820770496a49
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159987"
---
# <a name="bc40033-non-cls-compliant-membername-is-not-allowed-in-a-cls-compliant-interface"></a><span data-ttu-id="58479-102">BC40033 : non conforme CLS \<membername> n’est pas autorisé dans une interface conforme CLS</span><span class="sxs-lookup"><span data-stu-id="58479-102">BC40033: Non-CLS-compliant \<membername> is not allowed in a CLS-compliant interface</span></span>

<span data-ttu-id="58479-103">Une propriété, une procédure ou un événement dans une interface est marqué comme `<CLSCompliant(True)>` lorsque l’interface elle-même est marquée comme `<CLSCompliant(False)>` ou n’est pas marquée.</span><span class="sxs-lookup"><span data-stu-id="58479-103">A property, procedure, or event in an interface is marked as `<CLSCompliant(True)>` when the interface itself is marked as `<CLSCompliant(False)>` or is not marked.</span></span>

 <span data-ttu-id="58479-104">Pour qu’une interface soit conforme à l' [indépendance du langage et aux composants de Language-Independent](../../../standard/language-independence-and-language-independent-components.md) (CLS), tous ses membres doivent être conformes.</span><span class="sxs-lookup"><span data-stu-id="58479-104">For an interface to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), all its members must be compliant.</span></span>

 <span data-ttu-id="58479-105">Quand vous appliquez l’attribut <xref:System.CLSCompliantAttribute> à un élément de programmation, vous affectez au paramètre `isCompliant` de l’attribut la valeur `True` ou `False` pour indiquer la conformité ou la non-conformité.</span><span class="sxs-lookup"><span data-stu-id="58479-105">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="58479-106">Il n’existe pas de valeur par défaut pour ce paramètre et vous devez fournir une valeur.</span><span class="sxs-lookup"><span data-stu-id="58479-106">There is no default for this parameter, and you must supply a value.</span></span>

 <span data-ttu-id="58479-107">Si vous n’appliquez pas <xref:System.CLSCompliantAttribute> à un élément, il est considéré comme étant non conforme.</span><span class="sxs-lookup"><span data-stu-id="58479-107">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>

 <span data-ttu-id="58479-108">Par défaut, ce message est un avertissement.</span><span class="sxs-lookup"><span data-stu-id="58479-108">By default, this message is a warning.</span></span> <span data-ttu-id="58479-109">Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="58479-109">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="58479-110">**ID d’erreur :** BC40033</span><span class="sxs-lookup"><span data-stu-id="58479-110">**Error ID:** BC40033</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="58479-111">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="58479-111">To correct this error</span></span>

- <span data-ttu-id="58479-112">Si la conformité CLS est requise et si vous contrôlez le code source de l’interface, marquez l’interface comme `<CLSCompliant(True)>` si tous ses membres étaient conformes.</span><span class="sxs-lookup"><span data-stu-id="58479-112">If you require CLS compliance and have control over the interface source code, mark the interface as `<CLSCompliant(True)>` if all its members are compliant.</span></span>

- <span data-ttu-id="58479-113">Si vous avez besoin de la conformité CLS et que vous n’avez pas le contrôle du code source de l’interface, ou s’il n’est pas qualifié pour être conforme, définissez ce membre dans une autre interface.</span><span class="sxs-lookup"><span data-stu-id="58479-113">If you require CLS compliance and do not have control over the interface source code, or if it does not qualify to be compliant, define this member within a different interface.</span></span>

- <span data-ttu-id="58479-114">Si vous avez besoin que ce membre reste dans son interface actuelle, supprimez <xref:System.CLSCompliantAttribute> de sa définition ou marquez-le comme `<CLSCompliant(False)>` .</span><span class="sxs-lookup"><span data-stu-id="58479-114">If you require that this member remain within its current interface, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span>

## <a name="see-also"></a><span data-ttu-id="58479-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="58479-115">See also</span></span>

- [<span data-ttu-id="58479-116">Interface (instruction)</span><span class="sxs-lookup"><span data-stu-id="58479-116">Interface Statement</span></span>](../statements/interface-statement.md)
