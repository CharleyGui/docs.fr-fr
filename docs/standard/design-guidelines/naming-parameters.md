---
title: Attribution d'un nom à des paramètres
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- parameters, names
- names [.NET Framework], parameters
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
ms.openlocfilehash: ebe2e2db4b109057bf576d4e18cfe511c657707e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743830"
---
# <a name="naming-parameters"></a><span data-ttu-id="afeef-102">Attribution d'un nom à des paramètres</span><span class="sxs-lookup"><span data-stu-id="afeef-102">Naming Parameters</span></span>
<span data-ttu-id="afeef-103">Au-delà de la raison évidente de la lisibilité, il est important de suivre les instructions pour les noms de paramètres, car les paramètres sont affichés dans la documentation et dans le concepteur quand les outils de conception visuelle proposent IntelliSense et la fonctionnalité de navigation des classes.</span><span class="sxs-lookup"><span data-stu-id="afeef-103">Beyond the obvious reason of readability, it is important to follow the guidelines for parameter names because parameters are displayed in documentation and in the designer when visual design tools provide Intellisense and class browsing functionality.</span></span>

 <span data-ttu-id="afeef-104">✔️ Utilisez camelCasing dans les noms de paramètres.</span><span class="sxs-lookup"><span data-stu-id="afeef-104">✔️ DO use camelCasing in parameter names.</span></span>

 <span data-ttu-id="afeef-105">✔️ Utilisez des noms de paramètres descriptifs.</span><span class="sxs-lookup"><span data-stu-id="afeef-105">✔️ DO use descriptive parameter names.</span></span>

 <span data-ttu-id="afeef-106">✔️ envisagez d’utiliser des noms basés sur la signification d’un paramètre plutôt que sur le type du paramètre.</span><span class="sxs-lookup"><span data-stu-id="afeef-106">✔️ CONSIDER using names based on a parameter’s meaning rather than the parameter’s type.</span></span>

### <a name="naming-operator-overload-parameters"></a><span data-ttu-id="afeef-107">Affectation de noms aux paramètres de surcharge d’opérateur</span><span class="sxs-lookup"><span data-stu-id="afeef-107">Naming Operator Overload Parameters</span></span>
 <span data-ttu-id="afeef-108">✔️ Utilisez `left` et `right` pour les noms de paramètre de surcharge d’opérateur binaire s’il n’y a aucune signification pour les paramètres.</span><span class="sxs-lookup"><span data-stu-id="afeef-108">✔️ DO use `left` and `right` for binary operator overload parameter names if there is no meaning to the parameters.</span></span>

 <span data-ttu-id="afeef-109">✔️ Utilisez `value` pour les noms de paramètre de surcharge d’opérateur unaire si les paramètres n’ont aucune signification.</span><span class="sxs-lookup"><span data-stu-id="afeef-109">✔️ DO use `value` for unary operator overload parameter names if there is no meaning to the parameters.</span></span>

 <span data-ttu-id="afeef-110">✔️ CONSIDÉRez les noms significatifs pour les paramètres de surcharge d’opérateur si cela ajoute une valeur significative.</span><span class="sxs-lookup"><span data-stu-id="afeef-110">✔️ CONSIDER meaningful names for operator overload parameters if doing so adds significant value.</span></span>

 <span data-ttu-id="afeef-111">❌ n’utilisez pas d’abréviations ou d’index numériques pour les noms de paramètre de surcharge d’opérateur.</span><span class="sxs-lookup"><span data-stu-id="afeef-111">❌ DO NOT use abbreviations or numeric indices for operator overload parameter names.</span></span>

 <span data-ttu-id="afeef-112">*Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="afeef-112">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="afeef-113">*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="afeef-113">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="afeef-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="afeef-114">See also</span></span>

- [<span data-ttu-id="afeef-115">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="afeef-115">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="afeef-116">Directives de nommage</span><span class="sxs-lookup"><span data-stu-id="afeef-116">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
