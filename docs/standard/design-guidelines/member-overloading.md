---
title: Surcharge de membre
ms.date: 10/22/2008
helpviewer_keywords:
- default arguments
- members [.NET Framework], overloaded
- member design guidelines [.NET Framework], overloading
- overloaded members
- signatures, members
ms.assetid: 964ba19e-8b94-4b5b-b1e3-5a0b531a0bb1
ms.openlocfilehash: 16e84f06ec388fe7e3c221f35c3e970b9b483ba5
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94820967"
---
# <a name="member-overloading"></a><span data-ttu-id="6056e-102">Surcharge de membre</span><span class="sxs-lookup"><span data-stu-id="6056e-102">Member Overloading</span></span>
<span data-ttu-id="6056e-103">La surcharge de membre consiste à créer deux membres ou plus sur le même type qui diffèrent uniquement par le nombre ou le type de paramètres, mais qui portent le même nom.</span><span class="sxs-lookup"><span data-stu-id="6056e-103">Member overloading means creating two or more members on the same type that differ only in the number or type of parameters but have the same name.</span></span> <span data-ttu-id="6056e-104">Par exemple, dans le code suivant, la `WriteLine` méthode est surchargée :</span><span class="sxs-lookup"><span data-stu-id="6056e-104">For example, in the following, the `WriteLine` method is overloaded:</span></span>

```csharp
public static class Console {
    public void WriteLine();
    public void WriteLine(string value);
    public void WriteLine(bool value);
    ...
}
```

 <span data-ttu-id="6056e-105">Étant donné que seules les méthodes, les constructeurs et les propriétés indexées peuvent avoir des paramètres, seuls ces membres peuvent être surchargés.</span><span class="sxs-lookup"><span data-stu-id="6056e-105">Because only methods, constructors, and indexed properties can have parameters, only those members can be overloaded.</span></span>

 <span data-ttu-id="6056e-106">La surcharge est l’une des techniques les plus importantes pour améliorer la convivialité, la productivité et la lisibilité des bibliothèques réutilisables.</span><span class="sxs-lookup"><span data-stu-id="6056e-106">Overloading is one of the most important techniques for improving usability, productivity, and readability of reusable libraries.</span></span> <span data-ttu-id="6056e-107">La surcharge sur le nombre de paramètres permet de fournir des versions plus simples des constructeurs et des méthodes.</span><span class="sxs-lookup"><span data-stu-id="6056e-107">Overloading on the number of parameters makes it possible to provide simpler versions of constructors and methods.</span></span> <span data-ttu-id="6056e-108">La surcharge sur le type de paramètre permet d’utiliser le même nom de membre pour les membres effectuant des opérations identiques sur un ensemble sélectionné de types différents.</span><span class="sxs-lookup"><span data-stu-id="6056e-108">Overloading on the parameter type makes it possible to use the same member name for members performing identical operations on a selected set of different types.</span></span>

 <span data-ttu-id="6056e-109">✔️ essayez d’utiliser des noms de paramètres descriptifs pour indiquer la valeur par défaut utilisée par les surcharges plus courtes.</span><span class="sxs-lookup"><span data-stu-id="6056e-109">✔️ DO try to use descriptive parameter names to indicate the default used by shorter overloads.</span></span>

 <span data-ttu-id="6056e-110">❌ Évitez la variation arbitraire des noms de paramètres dans les surcharges.</span><span class="sxs-lookup"><span data-stu-id="6056e-110">❌ AVOID arbitrarily varying parameter names in overloads.</span></span> <span data-ttu-id="6056e-111">Si un paramètre d’une surcharge représente la même entrée qu’un paramètre dans une autre surcharge, les paramètres doivent avoir le même nom.</span><span class="sxs-lookup"><span data-stu-id="6056e-111">If a parameter in one overload represents the same input as a parameter in another overload, the parameters should have the same name.</span></span>

 <span data-ttu-id="6056e-112">❌ Évitez d’être incohérent dans l’ordre des paramètres dans les membres surchargés.</span><span class="sxs-lookup"><span data-stu-id="6056e-112">❌ AVOID being inconsistent in the ordering of parameters in overloaded members.</span></span> <span data-ttu-id="6056e-113">Les paramètres portant le même nom doivent apparaître à la même position dans toutes les surcharges.</span><span class="sxs-lookup"><span data-stu-id="6056e-113">Parameters with the same name should appear in the same position in all overloads.</span></span>

 <span data-ttu-id="6056e-114">✔️ Effectuez uniquement la surcharge virtuelle la plus longue (si l’extensibilité est requise).</span><span class="sxs-lookup"><span data-stu-id="6056e-114">✔️ DO make only the longest overload virtual (if extensibility is required).</span></span> <span data-ttu-id="6056e-115">Les surcharges plus courtes doivent simplement appeler une surcharge plus longue.</span><span class="sxs-lookup"><span data-stu-id="6056e-115">Shorter overloads should simply call through to a longer overload.</span></span>

 <span data-ttu-id="6056e-116">❌ N’utilisez pas `ref` `out` les modificateurs ou pour surcharger des membres.</span><span class="sxs-lookup"><span data-stu-id="6056e-116">❌ DO NOT use `ref` or `out` modifiers to overload members.</span></span>

 <span data-ttu-id="6056e-117">Certains langages ne peuvent pas résoudre les appels aux surcharges de ce type.</span><span class="sxs-lookup"><span data-stu-id="6056e-117">Some languages cannot resolve calls to overloads like this.</span></span> <span data-ttu-id="6056e-118">En outre, ces surcharges ont généralement une sémantique complètement différente et ne doivent probablement pas être des surcharges, mais deux méthodes distinctes à la place.</span><span class="sxs-lookup"><span data-stu-id="6056e-118">In addition, such overloads usually have completely different semantics and probably should not be overloads but two separate methods instead.</span></span>

 <span data-ttu-id="6056e-119">❌ N’ont pas de surcharges avec des paramètres à la même position et des types similaires encore avec une sémantique différente.</span><span class="sxs-lookup"><span data-stu-id="6056e-119">❌ DO NOT have overloads with parameters at the same position and similar types yet with different semantics.</span></span>

 <span data-ttu-id="6056e-120">✔️ autoriser `null` à être passé pour des arguments facultatifs.</span><span class="sxs-lookup"><span data-stu-id="6056e-120">✔️ DO  allow `null` to be passed for optional arguments.</span></span>

 <span data-ttu-id="6056e-121">✔️ Utilisez la surcharge des membres plutôt que de définir des membres avec des arguments par défaut.</span><span class="sxs-lookup"><span data-stu-id="6056e-121">✔️ DO use member overloading rather than defining members with default arguments.</span></span>

 <span data-ttu-id="6056e-122">Les arguments par défaut ne sont pas conformes CLS.</span><span class="sxs-lookup"><span data-stu-id="6056e-122">Default arguments are not CLS compliant.</span></span>

 <span data-ttu-id="6056e-123">*Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="6056e-123">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="6056e-124">*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="6056e-124">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="6056e-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6056e-125">See also</span></span>

- [<span data-ttu-id="6056e-126">Recommandations en matière de conception de membres</span><span class="sxs-lookup"><span data-stu-id="6056e-126">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="6056e-127">Directives de conception d’infrastructure</span><span class="sxs-lookup"><span data-stu-id="6056e-127">Framework Design Guidelines</span></span>](index.md)
