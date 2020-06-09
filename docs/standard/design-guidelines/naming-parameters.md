---
title: Attribution d'un nom à des paramètres
description: Découvrez les instructions relatives à la dénomination des paramètres. Par exemple, utilisez des noms de paramètres descriptifs & casse mixte, & envisagez d’attribuer un nom en fonction de la signification au lieu de type.
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- parameters, names
- names [.NET Framework], parameters
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
ms.openlocfilehash: 54f37c4d6a0f9a6931fa69d612bf0e45bf1f2ce7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84583516"
---
# <a name="naming-parameters"></a><span data-ttu-id="0a7cd-104">Attribution d'un nom à des paramètres</span><span class="sxs-lookup"><span data-stu-id="0a7cd-104">Naming Parameters</span></span>
<span data-ttu-id="0a7cd-105">Au-delà de la raison évidente de la lisibilité, il est important de suivre les instructions pour les noms de paramètres, car les paramètres sont affichés dans la documentation et dans le concepteur quand les outils de conception visuelle proposent IntelliSense et la fonctionnalité de navigation des classes.</span><span class="sxs-lookup"><span data-stu-id="0a7cd-105">Beyond the obvious reason of readability, it is important to follow the guidelines for parameter names because parameters are displayed in documentation and in the designer when visual design tools provide Intellisense and class browsing functionality.</span></span>

 <span data-ttu-id="0a7cd-106">✔️ Utilisez camelCasing dans les noms de paramètres.</span><span class="sxs-lookup"><span data-stu-id="0a7cd-106">✔️ DO use camelCasing in parameter names.</span></span>

 <span data-ttu-id="0a7cd-107">✔️ Utilisez des noms de paramètres descriptifs.</span><span class="sxs-lookup"><span data-stu-id="0a7cd-107">✔️ DO use descriptive parameter names.</span></span>

 <span data-ttu-id="0a7cd-108">✔️ envisagez d’utiliser des noms basés sur la signification d’un paramètre plutôt que sur le type du paramètre.</span><span class="sxs-lookup"><span data-stu-id="0a7cd-108">✔️ CONSIDER using names based on a parameter’s meaning rather than the parameter’s type.</span></span>

### <a name="naming-operator-overload-parameters"></a><span data-ttu-id="0a7cd-109">Affectation de noms aux paramètres de surcharge d’opérateur</span><span class="sxs-lookup"><span data-stu-id="0a7cd-109">Naming Operator Overload Parameters</span></span>
 <span data-ttu-id="0a7cd-110">✔️ Utilisez `left` et `right` pour les noms de paramètre de surcharge d’opérateur binaire s’il n’y a aucune signification pour les paramètres.</span><span class="sxs-lookup"><span data-stu-id="0a7cd-110">✔️ DO use `left` and `right` for binary operator overload parameter names if there is no meaning to the parameters.</span></span>

 <span data-ttu-id="0a7cd-111">✔️ Utilisez `value` pour les noms de paramètre de surcharge d’opérateur unaire si les paramètres n’ont aucune signification.</span><span class="sxs-lookup"><span data-stu-id="0a7cd-111">✔️ DO use `value` for unary operator overload parameter names if there is no meaning to the parameters.</span></span>

 <span data-ttu-id="0a7cd-112">✔️ CONSIDÉRez les noms significatifs pour les paramètres de surcharge d’opérateur si cela ajoute une valeur significative.</span><span class="sxs-lookup"><span data-stu-id="0a7cd-112">✔️ CONSIDER meaningful names for operator overload parameters if doing so adds significant value.</span></span>

 <span data-ttu-id="0a7cd-113">❌N’utilisez pas d’abréviations ou d’index numériques pour les noms de paramètre de surcharge d’opérateur.</span><span class="sxs-lookup"><span data-stu-id="0a7cd-113">❌ DO NOT use abbreviations or numeric indices for operator overload parameter names.</span></span>

 <span data-ttu-id="0a7cd-114">*Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="0a7cd-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="0a7cd-115">*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="0a7cd-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="0a7cd-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0a7cd-116">See also</span></span>

- [<span data-ttu-id="0a7cd-117">Directives de conception d’infrastructure</span><span class="sxs-lookup"><span data-stu-id="0a7cd-117">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="0a7cd-118">Instructions d’affectation de noms</span><span class="sxs-lookup"><span data-stu-id="0a7cd-118">Naming Guidelines</span></span>](naming-guidelines.md)
