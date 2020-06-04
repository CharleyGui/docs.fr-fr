---
title: "'<elementname>' est obsolète (avertissement Visual Basic)"
ms.date: 07/20/2015
f1_keywords:
- vbc40008
- bc40008
helpviewer_keywords:
- BC40008
ms.assetid: 729e3eb5-76ac-4c55-9fdd-78350e0de55e
ms.openlocfilehash: 7914bc859966e17f3da41c9a13a01573b31baf91
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409671"
---
# <a name="elementname-is-obsolete-visual-basic-warning"></a><span data-ttu-id="c4248-102">'\<elementname>' est obsolète (avertissement Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c4248-102">'\<elementname>' is obsolete (Visual Basic Warning)</span></span>
<span data-ttu-id="c4248-103">Une instruction tente d’accéder à un élément de programmation qui a été marqué avec l’attribut <xref:System.ObsoleteAttribute> et la directive pour le traiter comme un avertissement.</span><span class="sxs-lookup"><span data-stu-id="c4248-103">A statement attempts to access a programming element which has been marked with the <xref:System.ObsoleteAttribute> attribute and the directive to treat it as a warning.</span></span>  
  
 <span data-ttu-id="c4248-104">Vous pouvez marquer un élément de programmation comme n’étant plus utilisé en lui appliquant <xref:System.ObsoleteAttribute> .</span><span class="sxs-lookup"><span data-stu-id="c4248-104">You can mark any programming element as being no longer in use by applying <xref:System.ObsoleteAttribute> to it.</span></span> <span data-ttu-id="c4248-105">Dans ce cas, vous pouvez affecter à la propriété <xref:System.ObsoleteAttribute.IsError%2A> de l’attribut la valeur `True` ou `False`.</span><span class="sxs-lookup"><span data-stu-id="c4248-105">If you do this, you can set the attribute's <xref:System.ObsoleteAttribute.IsError%2A> property to either `True` or `False`.</span></span> <span data-ttu-id="c4248-106">Si vous lui affectez la valeur `True`, le compilateur traite une tentative d’utilisation de l’élément comme une erreur.</span><span class="sxs-lookup"><span data-stu-id="c4248-106">If you set it to `True`, the compiler treats an attempt to use the element as an error.</span></span> <span data-ttu-id="c4248-107">Si vous lui affectez la valeur `False`ou si vous laissez la valeur par défaut `False`, le compilateur émet un avertissement en cas de tentative d’utilisation de l’élément.</span><span class="sxs-lookup"><span data-stu-id="c4248-107">If you set it to `False`, or let it default to `False`, the compiler issues a warning if there is an attempt to use the element.</span></span>  
  
 <span data-ttu-id="c4248-108">Par défaut, ce message est un avertissement, car la propriété <xref:System.ObsoleteAttribute.IsError%2A> de <xref:System.ObsoleteAttribute> a la valeur `False`.</span><span class="sxs-lookup"><span data-stu-id="c4248-108">By default, this message is a warning, because the <xref:System.ObsoleteAttribute.IsError%2A> property of <xref:System.ObsoleteAttribute> is `False`.</span></span> <span data-ttu-id="c4248-109">Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="c4248-109">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="c4248-110">**ID d’erreur :** BC40008</span><span class="sxs-lookup"><span data-stu-id="c4248-110">**Error ID:** BC40008</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c4248-111">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="c4248-111">To correct this error</span></span>  
  
- <span data-ttu-id="c4248-112">Vérifiez que le nom de l’élément est orthographié correctement dans la référence du code source.</span><span class="sxs-lookup"><span data-stu-id="c4248-112">Ensure that the source-code reference is spelling the element name correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4248-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c4248-113">See also</span></span>

- [<span data-ttu-id="c4248-114">Vue d’ensemble des attributs</span><span class="sxs-lookup"><span data-stu-id="c4248-114">Attributes overview</span></span>](../../programming-guide/concepts/attributes/index.md)
