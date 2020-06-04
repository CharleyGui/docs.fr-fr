---
title: "La première instruction de ce 'Sub New' doit être un appel explicite à 'MyBase.New' ou 'MyClass.New', car le '<constructorname>' dans la classe de base '<baseclassname>' de '<derivedclassname>' est marqué comme obsolète : '<errormessage>'"
ms.date: 07/20/2015
f1_keywords:
- vbc30920
- bc30920
helpviewer_keywords:
- BC30920
ms.assetid: e47dc755-4294-4368-b813-2177b7677957
ms.openlocfilehash: 33dd15e3f5f5538963597f2b00f4214895e1f47a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403003"
---
# <a name="first-statement-of-this-sub-new-must-be-an-explicit-call-to-mybasenew-or-myclassnew-because-the-constructorname-in-the-base-class-baseclassname-of-derivedclassname-is-marked-obsolete-errormessage"></a><span data-ttu-id="654ba-102">La première instruction de ce 'Sub New' doit être un appel explicite à 'MyBase.New' ou 'MyClass.New', car le '\<constructorname>' dans la classe de base '\<baseclassname>' de '\<derivedclassname>' est marqué comme obsolète : '\<errormessage>'</span><span class="sxs-lookup"><span data-stu-id="654ba-102">First statement of this 'Sub New' must be an explicit call to 'MyBase.New' or 'MyClass.New' because the '\<constructorname>' in the base class '\<baseclassname>' of '\<derivedclassname>' is marked obsolete: '\<errormessage>'</span></span>
<span data-ttu-id="654ba-103">Un constructeur de classe n’appelle pas explicitement un constructeur de classe de base et le constructeur de classe de base implicite est marqué avec l’attribut <xref:System.ObsoleteAttribute> et la directive pour le traiter comme une erreur.</span><span class="sxs-lookup"><span data-stu-id="654ba-103">A class constructor does not explicitly call a base class constructor, and the implicit base class constructor is marked with the <xref:System.ObsoleteAttribute> attribute and the directive to treat it as an error.</span></span>  
  
 <span data-ttu-id="654ba-104">Lorsqu’un constructeur de classe dérivée n’appelle pas de constructeur de classe de base, Visual Basic tente de générer un appel implicite à un constructeur de classe de base sans paramètre.</span><span class="sxs-lookup"><span data-stu-id="654ba-104">When a derived class constructor does not call a base class constructor, Visual Basic attempts to generate an implicit call to a parameterless base class constructor.</span></span> <span data-ttu-id="654ba-105">S’il n’existe aucun constructeur accessible dans la classe de base qui peut être appelé sans arguments, Visual Basic ne peut pas générer un appel implicite.</span><span class="sxs-lookup"><span data-stu-id="654ba-105">If there is no accessible constructor in the base class that can be called without arguments, Visual Basic cannot generate an implicit call.</span></span> <span data-ttu-id="654ba-106">Dans ce cas, le constructeur requis est marqué avec l' <xref:System.ObsoleteAttribute> attribut, donc Visual Basic ne peut pas l’appeler.</span><span class="sxs-lookup"><span data-stu-id="654ba-106">In this case, the required constructor is marked with the <xref:System.ObsoleteAttribute> attribute, so Visual Basic cannot call it.</span></span>  
  
 <span data-ttu-id="654ba-107">Vous pouvez marquer un élément de programmation comme n’étant plus utilisé en lui appliquant <xref:System.ObsoleteAttribute> .</span><span class="sxs-lookup"><span data-stu-id="654ba-107">You can mark any programming element as being no longer in use by applying <xref:System.ObsoleteAttribute> to it.</span></span> <span data-ttu-id="654ba-108">Dans ce cas, vous pouvez affecter à la propriété <xref:System.ObsoleteAttribute.IsError%2A> de l’attribut la valeur `True` ou `False`.</span><span class="sxs-lookup"><span data-stu-id="654ba-108">If you do this, you can set the attribute's <xref:System.ObsoleteAttribute.IsError%2A> property to either `True` or `False`.</span></span> <span data-ttu-id="654ba-109">Si vous lui affectez la valeur `True`, le compilateur traite une tentative d’utilisation de l’élément comme une erreur.</span><span class="sxs-lookup"><span data-stu-id="654ba-109">If you set it to `True`, the compiler treats an attempt to use the element as an error.</span></span> <span data-ttu-id="654ba-110">Si vous lui affectez la valeur `False`ou si vous laissez la valeur par défaut `False`, le compilateur émet un avertissement en cas de tentative d’utilisation de l’élément.</span><span class="sxs-lookup"><span data-stu-id="654ba-110">If you set it to `False`, or let it default to `False`, the compiler issues a warning if there is an attempt to use the element.</span></span>  
  
 <span data-ttu-id="654ba-111">**ID d’erreur :** BC30920</span><span class="sxs-lookup"><span data-stu-id="654ba-111">**Error ID:** BC30920</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="654ba-112">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="654ba-112">To correct this error</span></span>  
  
1. <span data-ttu-id="654ba-113">Examinez le message d’erreur mentionné et prenez les mesures nécessaires.</span><span class="sxs-lookup"><span data-stu-id="654ba-113">Examine the quoted error message and take appropriate action.</span></span>  
  
2. <span data-ttu-id="654ba-114">Incluez un appel à `MyBase.New()` ou `MyClass.New()` en tant que première instruction de `Sub New` dans la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="654ba-114">Include a call to `MyBase.New()` or `MyClass.New()` as the first statement of the `Sub New` in the derived class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="654ba-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="654ba-115">See also</span></span>

- [<span data-ttu-id="654ba-116">Vue d’ensemble des attributs</span><span class="sxs-lookup"><span data-stu-id="654ba-116">Attributes overview</span></span>](../../programming-guide/concepts/attributes/index.md)
