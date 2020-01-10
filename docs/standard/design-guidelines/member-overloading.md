---
title: Surcharge de membre
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- default arguments
- members [.NET Framework], overloaded
- member design guidelines [.NET Framework], overloading
- overloaded members
- signatures, members
ms.assetid: 964ba19e-8b94-4b5b-b1e3-5a0b531a0bb1
ms.openlocfilehash: e7decab042dd1ee36beacb18956e175196cd112c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709281"
---
# <a name="member-overloading"></a><span data-ttu-id="f122c-102">Surcharge de membre</span><span class="sxs-lookup"><span data-stu-id="f122c-102">Member Overloading</span></span>
<span data-ttu-id="f122c-103">La surcharge de membre consiste à créer deux membres ou plus sur le même type qui diffèrent uniquement par le nombre ou le type de paramètres, mais qui portent le même nom.</span><span class="sxs-lookup"><span data-stu-id="f122c-103">Member overloading means creating two or more members on the same type that differ only in the number or type of parameters but have the same name.</span></span> <span data-ttu-id="f122c-104">Par exemple, dans le code suivant, la méthode `WriteLine` est surchargée :</span><span class="sxs-lookup"><span data-stu-id="f122c-104">For example, in the following, the `WriteLine` method is overloaded:</span></span>  
  
```csharp  
public static class Console {  
    public void WriteLine();  
    public void WriteLine(string value);  
    public void WriteLine(bool value);  
    ...  
}  
```  
  
 <span data-ttu-id="f122c-105">Étant donné que seules les méthodes, les constructeurs et les propriétés indexées peuvent avoir des paramètres, seuls ces membres peuvent être surchargés.</span><span class="sxs-lookup"><span data-stu-id="f122c-105">Because only methods, constructors, and indexed properties can have parameters, only those members can be overloaded.</span></span>  
  
 <span data-ttu-id="f122c-106">La surcharge est l’une des techniques les plus importantes pour améliorer la convivialité, la productivité et la lisibilité des bibliothèques réutilisables.</span><span class="sxs-lookup"><span data-stu-id="f122c-106">Overloading is one of the most important techniques for improving usability, productivity, and readability of reusable libraries.</span></span> <span data-ttu-id="f122c-107">La surcharge sur le nombre de paramètres permet de fournir des versions plus simples des constructeurs et des méthodes.</span><span class="sxs-lookup"><span data-stu-id="f122c-107">Overloading on the number of parameters makes it possible to provide simpler versions of constructors and methods.</span></span> <span data-ttu-id="f122c-108">La surcharge sur le type de paramètre permet d’utiliser le même nom de membre pour les membres effectuant des opérations identiques sur un ensemble sélectionné de types différents.</span><span class="sxs-lookup"><span data-stu-id="f122c-108">Overloading on the parameter type makes it possible to use the same member name for members performing identical operations on a selected set of different types.</span></span>  
  
 <span data-ttu-id="f122c-109">**✓ DO** essayez d’utiliser des noms de paramètres descriptifs pour indiquer la valeur par défaut utilisée par les surcharges plus courts.</span><span class="sxs-lookup"><span data-stu-id="f122c-109">**✓ DO** try to use descriptive parameter names to indicate the default used by shorter overloads.</span></span>  
  
 <span data-ttu-id="f122c-110">**X AVOID** Variant de façon arbitraire les noms de paramètres dans les surcharges.</span><span class="sxs-lookup"><span data-stu-id="f122c-110">**X AVOID** arbitrarily varying parameter names in overloads.</span></span> <span data-ttu-id="f122c-111">Si un paramètre d’une surcharge représente la même entrée qu’un paramètre dans une autre surcharge, les paramètres doivent avoir le même nom.</span><span class="sxs-lookup"><span data-stu-id="f122c-111">If a parameter in one overload represents the same input as a parameter in another overload, the parameters should have the same name.</span></span>  
  
 <span data-ttu-id="f122c-112">**X AVOID** incohérent dans l’ordre des paramètres de surcharge membres.</span><span class="sxs-lookup"><span data-stu-id="f122c-112">**X AVOID** being inconsistent in the ordering of parameters in overloaded members.</span></span> <span data-ttu-id="f122c-113">Les paramètres portant le même nom doivent apparaître à la même position dans toutes les surcharges.</span><span class="sxs-lookup"><span data-stu-id="f122c-113">Parameters with the same name should appear in the same position in all overloads.</span></span>  
  
 <span data-ttu-id="f122c-114">**✓ DO** créer uniquement la surcharge la plus longue virtuelle (si l’extensibilité est requise).</span><span class="sxs-lookup"><span data-stu-id="f122c-114">**✓ DO** make only the longest overload virtual (if extensibility is required).</span></span> <span data-ttu-id="f122c-115">Les surcharges plus courtes doivent simplement appeler une surcharge plus longue.</span><span class="sxs-lookup"><span data-stu-id="f122c-115">Shorter overloads should simply call through to a longer overload.</span></span>  
  
 <span data-ttu-id="f122c-116">**X DO NOT** utiliser `ref` ou `out` modificateurs pour surcharger les membres.</span><span class="sxs-lookup"><span data-stu-id="f122c-116">**X DO NOT** use `ref` or `out` modifiers to overload members.</span></span>  
  
 <span data-ttu-id="f122c-117">Certains langages ne peuvent pas résoudre les appels aux surcharges de ce type.</span><span class="sxs-lookup"><span data-stu-id="f122c-117">Some languages cannot resolve calls to overloads like this.</span></span> <span data-ttu-id="f122c-118">En outre, ces surcharges ont généralement une sémantique complètement différente et ne doivent probablement pas être des surcharges, mais deux méthodes distinctes à la place.</span><span class="sxs-lookup"><span data-stu-id="f122c-118">In addition, such overloads usually have completely different semantics and probably should not be overloads but two separate methods instead.</span></span>  
  
 <span data-ttu-id="f122c-119">**X DO NOT** ont des surcharges avec des paramètres à la même position et les types semblables, mais avec une sémantique différente.</span><span class="sxs-lookup"><span data-stu-id="f122c-119">**X DO NOT** have overloads with parameters at the same position and similar types yet with different semantics.</span></span>  
  
 <span data-ttu-id="f122c-120">**✓ DO** autoriser `null` à passer les arguments facultatifs.</span><span class="sxs-lookup"><span data-stu-id="f122c-120">**✓ DO**  allow `null` to be passed for optional arguments.</span></span>  
  
 <span data-ttu-id="f122c-121">**✓ DO** utiliser membre surcharge plutôt que de définir des membres avec des arguments par défaut.</span><span class="sxs-lookup"><span data-stu-id="f122c-121">**✓ DO** use member overloading rather than defining members with default arguments.</span></span>  
  
 <span data-ttu-id="f122c-122">Les arguments par défaut ne sont pas conformes CLS.</span><span class="sxs-lookup"><span data-stu-id="f122c-122">Default arguments are not CLS compliant.</span></span>  
  
 <span data-ttu-id="f122c-123">*Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="f122c-123">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="f122c-124">*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="f122c-124">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f122c-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f122c-125">See also</span></span>

- [<span data-ttu-id="f122c-126">Instructions de conception des membres</span><span class="sxs-lookup"><span data-stu-id="f122c-126">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)
- [<span data-ttu-id="f122c-127">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f122c-127">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
