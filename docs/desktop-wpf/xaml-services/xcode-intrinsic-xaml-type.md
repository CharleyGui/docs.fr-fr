---
title: x:Code, type XAML intrinsèque
ms.date: 03/30/2017
f1_keywords:
- Code
- x:Code
- xCode
helpviewer_keywords:
- Code directive in XAML [XAML Services]
- x:Code XAML directive element [XAML Services]
- XAML [XAML Services], x:Code directive element
ms.assetid: 87986b13-1a2e-4830-ae36-15f9dc5629e8
ms.openlocfilehash: 4da72ed630c1df001e3fd6c7e55f866b94c4d9b1
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071555"
---
# <a name="xcode-intrinsic-xaml-type"></a><span data-ttu-id="2945b-102">x:Code, type XAML intrinsèque</span><span class="sxs-lookup"><span data-stu-id="2945b-102">x:Code Intrinsic XAML Type</span></span>
<span data-ttu-id="2945b-103">Permet le placement du code dans une production XAML.</span><span class="sxs-lookup"><span data-stu-id="2945b-103">Allows placement of code within a XAML production.</span></span> <span data-ttu-id="2945b-104">Ce code peut être compilé par n’importe quelle implémentation de processeur XAML qui compile XAML, soit laissé dans la production XAML pour des utilisations ultérieures telles que l’interprétation par un temps d’exécution.</span><span class="sxs-lookup"><span data-stu-id="2945b-104">Such code can either be compiled by any XAML processor implementation that compiles XAML, or left in the XAML production for later uses such as interpretation by a runtime.</span></span>

## <a name="xaml-object-element-usage"></a><span data-ttu-id="2945b-105">Utilisation d'éléments objet XAML</span><span class="sxs-lookup"><span data-stu-id="2945b-105">XAML Object Element Usage</span></span>

```xaml
<x:Code>
   // code instructions, usually enclosed by CDATA...
</x:Code>
```

## <a name="remarks"></a><span data-ttu-id="2945b-106">Notes</span><span class="sxs-lookup"><span data-stu-id="2945b-106">Remarks</span></span>

<span data-ttu-id="2945b-107">Le code `x:Code` dans l’élément de directive XAML est toujours interprété dans l’espace de nom XML général et les espaces de nom XAML fournis.</span><span class="sxs-lookup"><span data-stu-id="2945b-107">The code within the `x:Code` XAML directive element is still interpreted within the general XML namespace and the XAML namespaces provided.</span></span> <span data-ttu-id="2945b-108">Par conséquent, il est généralement nécessaire `x:Code` d’enfermer le code utilisé à l’intérieur d’un `CDATA` segment.</span><span class="sxs-lookup"><span data-stu-id="2945b-108">Therefore, it is usually necessary to enclose the code used for `x:Code` inside a `CDATA` segment.</span></span>

<span data-ttu-id="2945b-109">`x:Code`n’est pas autorisé pour tous les mécanismes de déploiement possibles d’une production XAML.</span><span class="sxs-lookup"><span data-stu-id="2945b-109">`x:Code` is not permitted for all possible deployment mechanisms of a XAML production.</span></span> <span data-ttu-id="2945b-110">Dans des cadres spécifiques (par exemple WPF), le code doit être compilé.</span><span class="sxs-lookup"><span data-stu-id="2945b-110">In specific frameworks (for example WPF) the code must be compiled.</span></span> <span data-ttu-id="2945b-111">Dans d’autres `x:Code` cadres, l’utilisation peut généralement être refusée.</span><span class="sxs-lookup"><span data-stu-id="2945b-111">In other frameworks, `x:Code` usage might be generally disallowed.</span></span>

<span data-ttu-id="2945b-112">Pour les cadres `x:Code` qui permettent le contenu géré, `x:Code` le compilateur de langage correct à utiliser pour le contenu est déterminé par les paramètres et les cibles du projet contenant qui est utilisé pour compiler l’application.</span><span class="sxs-lookup"><span data-stu-id="2945b-112">For frameworks that permit managed `x:Code` content, the correct language compiler to use for `x:Code` content is determined by settings and targets of the containing project that is used to compile the application.</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="2945b-113">Remarques sur l'utilisation de WPF</span><span class="sxs-lookup"><span data-stu-id="2945b-113">WPF Usage Notes</span></span>

<span data-ttu-id="2945b-114">Le code `x:Code` déclaré à l’intérieur du FPM comporte plusieurs limites notables :</span><span class="sxs-lookup"><span data-stu-id="2945b-114">Code declared within `x:Code` for WPF has several notable limitations:</span></span>

- <span data-ttu-id="2945b-115">L’élément `x:Code` directive doit être un élément enfant immédiat de l’élément racine de la production XAML.</span><span class="sxs-lookup"><span data-stu-id="2945b-115">The `x:Code` directive element must be an immediate child element of the root element of the XAML production.</span></span>

- <span data-ttu-id="2945b-116">[x : La directive de classe](xclass-directive.md) doit être fournie sur l’élément racine parent.</span><span class="sxs-lookup"><span data-stu-id="2945b-116">[x:Class Directive](xclass-directive.md) must be provided on the parent root element.</span></span>

- <span data-ttu-id="2945b-117">Le code `x:Code` placé à l’intérieur sera traité par compilation pour être dans le cadre de la classe partielle qui est déjà en cours de création pour cette page XAML.</span><span class="sxs-lookup"><span data-stu-id="2945b-117">The code placed within `x:Code` will be treated by compilation to be within the scope of the partial class that is already being created for that XAML page.</span></span> <span data-ttu-id="2945b-118">Par conséquent, tout le code que vous définissez doit être membre ou variables de cette classe partielle.</span><span class="sxs-lookup"><span data-stu-id="2945b-118">Therefore all code you define must be members or variables of that partial class.</span></span>

- <span data-ttu-id="2945b-119">Vous ne pouvez pas définir des classes supplémentaires, sauf en nicher une classe à l’intérieur de la classe partielle (la nidification est autorisée, mais elle n’est pas typique parce que les classes imbriquées ne peuvent pas être référencées dans XAML).</span><span class="sxs-lookup"><span data-stu-id="2945b-119">You cannot define additional classes, other than by nesting a class inside the partial class (nesting is allowed, but it is not typical because nested classes cannot be referenced in XAML).</span></span> <span data-ttu-id="2945b-120">Les espaces de noms CLR autres que l’espace nom qui est utilisé pour la classe partielle existante ne peuvent pas être définis ou ajoutés.</span><span class="sxs-lookup"><span data-stu-id="2945b-120">CLR namespaces other than the namespace that is used for the existing partial class cannot be defined or added to.</span></span>

- <span data-ttu-id="2945b-121">Les références à des entités de code en dehors de l’espace de nom CLR de classe partielle doivent toutes être entièrement qualifiées.</span><span class="sxs-lookup"><span data-stu-id="2945b-121">References to code entities outside the partial class CLR namespace must all be fully qualified.</span></span> <span data-ttu-id="2945b-122">Si les membres déclarés remplacent les membres de la classe partielle, cela doit être spécifié avec le mot clé de substitution spécifique à la langue.</span><span class="sxs-lookup"><span data-stu-id="2945b-122">If members being declared are overrides to the partial class overridable members, this must be specified with the language-specific override keyword.</span></span> <span data-ttu-id="2945b-123">Si les `x:Code` membres déclarés en conflit de portée avec les membres de la classe partielle créé à partir de la XAML, de telle sorte que le compilateur signale le conflit, le fichier XAML ne peut pas compiler ou charger.</span><span class="sxs-lookup"><span data-stu-id="2945b-123">If members declared in `x:Code` scope conflict with members of the partial class created out of the XAML, in such a way that the compiler reports the conflict, the XAML file cannot compile or load.</span></span>

## <a name="see-also"></a><span data-ttu-id="2945b-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2945b-124">See also</span></span>

- [<span data-ttu-id="2945b-125">x:Class, directive</span><span class="sxs-lookup"><span data-stu-id="2945b-125">x:Class Directive</span></span>](xclass-directive.md)
- [<span data-ttu-id="2945b-126">Code-behind et XAML dans WPF</span><span class="sxs-lookup"><span data-stu-id="2945b-126">Code-Behind and XAML in WPF</span></span>](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [<span data-ttu-id="2945b-127">Vue d’ensemble du langage XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="2945b-127">XAML Overview (WPF)</span></span>](../fundamentals/xaml.md)
