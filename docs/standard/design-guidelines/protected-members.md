---
title: Membres protégés
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- members [.NET Framework], protected
- protected members
- classes [.NET Framework], unsealed
- classes [.NET Framework], protected members
- unsealed classes
- customizing class behavior
ms.assetid: aa0b58ee-3956-494d-ab48-471ae5db8740
ms.openlocfilehash: 44d342662e1aaeb51f14470f354f2dadd9a6f18d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743646"
---
# <a name="protected-members"></a><span data-ttu-id="15ce2-102">Membres protégés</span><span class="sxs-lookup"><span data-stu-id="15ce2-102">Protected Members</span></span>
<span data-ttu-id="15ce2-103">Les membres protégés par eux-mêmes ne fournissent pas d’extensibilité, mais ils peuvent rendre l’extensibilité à l’aide d’une sous-classe plus puissante.</span><span class="sxs-lookup"><span data-stu-id="15ce2-103">Protected members by themselves do not provide any extensibility, but they can make extensibility through subclassing more powerful.</span></span> <span data-ttu-id="15ce2-104">Ils peuvent être utilisés pour exposer des options de personnalisation avancées sans compliquer inutilement l’interface publique principale.</span><span class="sxs-lookup"><span data-stu-id="15ce2-104">They can be used to expose advanced customization options without unnecessarily complicating the main public interface.</span></span>

 <span data-ttu-id="15ce2-105">Les concepteurs de Framework doivent être vigilants avec les membres protégés, car le nom « protégé » peut avoir un sens de sécurité faux.</span><span class="sxs-lookup"><span data-stu-id="15ce2-105">Framework designers need to be careful with protected members because the name "protected" can give a false sense of security.</span></span> <span data-ttu-id="15ce2-106">Tout le monde peut sous-faire une classe non scellée et accéder à des membres protégés, de sorte que toutes les pratiques de codage défensives utilisées pour les membres publics s’appliquent aux membres protégés.</span><span class="sxs-lookup"><span data-stu-id="15ce2-106">Anyone is able to subclass an unsealed class and access protected members, and so all the same defensive coding practices used for public members apply to protected members.</span></span>

 <span data-ttu-id="15ce2-107">✔️ envisagez d’utiliser des membres protégés pour une personnalisation avancée.</span><span class="sxs-lookup"><span data-stu-id="15ce2-107">✔️ CONSIDER using protected members for advanced customization.</span></span>

 <span data-ttu-id="15ce2-108">✔️ Traitez les membres protégés dans des classes non scellées comme étant publics dans le cadre de la sécurité, de la documentation et de l’analyse de compatibilité.</span><span class="sxs-lookup"><span data-stu-id="15ce2-108">✔️ DO treat protected members in unsealed classes as public for the purpose of security, documentation, and compatibility analysis.</span></span>

 <span data-ttu-id="15ce2-109">Tout le monde peut hériter d’une classe et accéder aux membres protégés.</span><span class="sxs-lookup"><span data-stu-id="15ce2-109">Anyone can inherit from a class and access the protected members.</span></span>

 <span data-ttu-id="15ce2-110">*Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="15ce2-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="15ce2-111">*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="15ce2-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="15ce2-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="15ce2-112">See also</span></span>

- [<span data-ttu-id="15ce2-113">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="15ce2-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="15ce2-114">Conception en vue de l’extensibilité</span><span class="sxs-lookup"><span data-stu-id="15ce2-114">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
