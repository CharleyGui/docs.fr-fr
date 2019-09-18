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
ms.openlocfilehash: 2b7713548b6269f079ef32b5bf1fe4fa630edcc8
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053791"
---
# <a name="xcode-intrinsic-xaml-type"></a><span data-ttu-id="1d53e-102">x:Code, type XAML intrinsèque</span><span class="sxs-lookup"><span data-stu-id="1d53e-102">x:Code Intrinsic XAML Type</span></span>
<span data-ttu-id="1d53e-103">Autorise le positionnement du code dans une production XAML.</span><span class="sxs-lookup"><span data-stu-id="1d53e-103">Allows placement of code within a XAML production.</span></span> <span data-ttu-id="1d53e-104">Ce code peut être compilé par n’importe quelle implémentation de processeur XAML qui compile XAML, ou laissé dans la production XAML pour des utilisations ultérieures telles que l’interprétation par un Runtime.</span><span class="sxs-lookup"><span data-stu-id="1d53e-104">Such code can either be compiled by any XAML processor implementation that compiles XAML, or left in the XAML production for later uses such as interpretation by a runtime.</span></span>  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="1d53e-105">Utilisation d'éléments objet XAML</span><span class="sxs-lookup"><span data-stu-id="1d53e-105">XAML Object Element Usage</span></span>  
  
```xaml  
<x:Code>  
   // code instructions, usually enclosed by CDATA...  
</x:Code>  
```  
  
## <a name="remarks"></a><span data-ttu-id="1d53e-106">Notes</span><span class="sxs-lookup"><span data-stu-id="1d53e-106">Remarks</span></span>  
 <span data-ttu-id="1d53e-107">Le code contenu dans `x:Code` l’élément de directive XAML est toujours interprété dans l’espace de noms XML général et dans les espaces de noms XAML fournis.</span><span class="sxs-lookup"><span data-stu-id="1d53e-107">The code within the `x:Code` XAML directive element is still interpreted within the general XML namespace and the XAML namespaces provided.</span></span> <span data-ttu-id="1d53e-108">Par conséquent, il est généralement nécessaire de placer le code utilisé `x:Code` à l' `CDATA` intérieur d’un segment.</span><span class="sxs-lookup"><span data-stu-id="1d53e-108">Therefore, it is usually necessary to enclose the code used for `x:Code` inside a `CDATA` segment.</span></span>  
  
 <span data-ttu-id="1d53e-109">`x:Code`n’est pas autorisé pour tous les mécanismes de déploiement possibles d’une production XAML.</span><span class="sxs-lookup"><span data-stu-id="1d53e-109">`x:Code` is not permitted for all possible deployment mechanisms of a XAML production.</span></span> <span data-ttu-id="1d53e-110">Dans des frameworks spécifiques (par exemple WPF), le code doit être compilé.</span><span class="sxs-lookup"><span data-stu-id="1d53e-110">In specific frameworks (for example WPF) the code must be compiled.</span></span> <span data-ttu-id="1d53e-111">Dans d’autres infrastructures, `x:Code` l’utilisation peut être généralement interdite.</span><span class="sxs-lookup"><span data-stu-id="1d53e-111">In other frameworks, `x:Code` usage might be generally disallowed.</span></span>  
  
 <span data-ttu-id="1d53e-112">Pour les infrastructures qui autorisent `x:Code` le contenu managé, le compilateur de langage approprié `x:Code` à utiliser pour le contenu est déterminé par les paramètres et les cibles du projet conteneur utilisé pour compiler l’application.</span><span class="sxs-lookup"><span data-stu-id="1d53e-112">For frameworks that permit managed `x:Code` content, the correct language compiler to use for `x:Code` content is determined by settings and targets of the containing project that is used to compile the application.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="1d53e-113">Remarques sur l’utilisation de WPF</span><span class="sxs-lookup"><span data-stu-id="1d53e-113">WPF Usage Notes</span></span>  
 <span data-ttu-id="1d53e-114">Le code déclaré `x:Code` dans pour WPF présente plusieurs limitations notables :</span><span class="sxs-lookup"><span data-stu-id="1d53e-114">Code declared within `x:Code` for WPF has several notable limitations:</span></span>  
  
- <span data-ttu-id="1d53e-115">L' `x:Code` élément directive doit être un élément enfant immédiat de l’élément racine de la production XAML.</span><span class="sxs-lookup"><span data-stu-id="1d53e-115">The `x:Code` directive element must be an immediate child element of the root element of the XAML production.</span></span>  
  
- <span data-ttu-id="1d53e-116">la [directive x :Class](x-class-directive.md) doit être fournie sur l’élément racine parent.</span><span class="sxs-lookup"><span data-stu-id="1d53e-116">[x:Class Directive](x-class-directive.md) must be provided on the parent root element.</span></span>  
  
- <span data-ttu-id="1d53e-117">Le code placé dans `x:Code` sera traité par compilation pour se trouver dans la portée de la classe partielle qui est déjà en cours de création pour cette page XAML.</span><span class="sxs-lookup"><span data-stu-id="1d53e-117">The code placed within `x:Code` will be treated by compilation to be within the scope of the partial class that is already being created for that XAML page.</span></span> <span data-ttu-id="1d53e-118">Par conséquent, tout le code que vous définissez doit être membre ou variables de cette classe partielle.</span><span class="sxs-lookup"><span data-stu-id="1d53e-118">Therefore all code you define must be members or variables of that partial class.</span></span>  
  
- <span data-ttu-id="1d53e-119">Vous ne pouvez pas définir des classes supplémentaires, à l’exception de l’imbrication d’une classe à l’intérieur de la classe partielle (l’imbrication est autorisée, mais elle n’est pas courante, car les classes imbriquées ne peuvent pas être référencées en XAML).</span><span class="sxs-lookup"><span data-stu-id="1d53e-119">You cannot define additional classes, other than by nesting a class inside the partial class (nesting is allowed, but it is not typical because nested classes cannot be referenced in XAML).</span></span> <span data-ttu-id="1d53e-120">Les espaces de noms CLR autres que l’espace de noms utilisé pour la classe partielle existante ne peuvent pas être définis ou ajoutés à.</span><span class="sxs-lookup"><span data-stu-id="1d53e-120">CLR namespaces other than the namespace that is used for the existing partial class cannot be defined or added to.</span></span>  
  
- <span data-ttu-id="1d53e-121">Les références aux entités de code en dehors de l’espace de noms CLR de la classe partielle doivent toutes être qualifiées complètes.</span><span class="sxs-lookup"><span data-stu-id="1d53e-121">References to code entities outside the partial class CLR namespace must all be fully qualified.</span></span> <span data-ttu-id="1d53e-122">Si les membres déclarés sont substitués aux membres substituables de classe partielle, il doit être spécifié avec le mot clé de substitution spécifique au langage.</span><span class="sxs-lookup"><span data-stu-id="1d53e-122">If members being declared are overrides to the partial class overridable members, this must be specified with the language-specific override keyword.</span></span> <span data-ttu-id="1d53e-123">Si les membres déclarés dans `x:Code` la portée sont en conflit avec les membres de la classe partielle créée à partir du code XAML, de telle sorte que le compilateur signale le conflit, le fichier XAML ne peut pas être compilé ou chargé.</span><span class="sxs-lookup"><span data-stu-id="1d53e-123">If members declared in `x:Code` scope conflict with members of the partial class created out of the XAML, in such a way that the compiler reports the conflict, the XAML file cannot compile or load.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d53e-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1d53e-124">See also</span></span>

- [<span data-ttu-id="1d53e-125">x:Class, directive</span><span class="sxs-lookup"><span data-stu-id="1d53e-125">x:Class Directive</span></span>](x-class-directive.md)
- [<span data-ttu-id="1d53e-126">Code-behind et XAML dans WPF</span><span class="sxs-lookup"><span data-stu-id="1d53e-126">Code-Behind and XAML in WPF</span></span>](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [<span data-ttu-id="1d53e-127">Vue d’ensemble du langage XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="1d53e-127">XAML Overview (WPF)</span></span>](../wpf/advanced/xaml-overview-wpf.md)
