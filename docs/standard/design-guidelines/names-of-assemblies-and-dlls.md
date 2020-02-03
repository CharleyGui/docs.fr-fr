---
title: Noms d'assemblys et de DLL
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], DLLs
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
- DLLs, names
ms.assetid: e800b610-31b4-4949-9c14-cb60e9f254be
ms.openlocfilehash: f3c5997f777c937e9726b271afa0ae6d7a19b37d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744173"
---
# <a name="names-of-assemblies-and-dlls"></a><span data-ttu-id="acfaf-102">Noms d'assemblys et de DLL</span><span class="sxs-lookup"><span data-stu-id="acfaf-102">Names of Assemblies and DLLs</span></span>
<span data-ttu-id="acfaf-103">Un assembly est l’unité de déploiement et d’identité des programmes de code managé.</span><span class="sxs-lookup"><span data-stu-id="acfaf-103">An assembly is the unit of deployment and identity for managed code programs.</span></span> <span data-ttu-id="acfaf-104">Bien que les assemblys puissent couvrir un ou plusieurs fichiers, en général un assembly mappe un à un avec une DLL.</span><span class="sxs-lookup"><span data-stu-id="acfaf-104">Although assemblies can span one or more files, typically an assembly maps one-to-one with a DLL.</span></span> <span data-ttu-id="acfaf-105">Par conséquent, cette section décrit uniquement les conventions d’affectation de noms de DLL, qui peuvent alors être mappées aux conventions d’affectation de noms d’assembly.</span><span class="sxs-lookup"><span data-stu-id="acfaf-105">Therefore, this section describes only DLL naming conventions, which then can be mapped to assembly naming conventions.</span></span>

 <span data-ttu-id="acfaf-106">✔️ Choisissez des noms pour vos dll d’assembly qui suggèrent de grands blocs de fonctionnalités, tels que System. Data.</span><span class="sxs-lookup"><span data-stu-id="acfaf-106">✔️ DO choose names for your assembly DLLs that suggest large chunks of functionality, such as System.Data.</span></span>

 <span data-ttu-id="acfaf-107">Les noms d’assemblys et de DLL ne doivent pas nécessairement correspondre aux noms d’espaces de noms, mais il est raisonnable de suivre le nom de l’espace de noms lors de l’attribution de noms aux assemblys.</span><span class="sxs-lookup"><span data-stu-id="acfaf-107">Assembly and DLL names don’t have to correspond to namespace names, but it is reasonable to follow the namespace name when naming assemblies.</span></span> <span data-ttu-id="acfaf-108">Une bonne règle empirique consiste à nommer la DLL en fonction du préfixe commun des espaces de noms contenus dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="acfaf-108">A good rule of thumb is to name the DLL based on the common prefix of the namespaces contained in the assembly.</span></span> <span data-ttu-id="acfaf-109">Par exemple, un assembly avec deux espaces de noms, `MyCompany.MyTechnology.FirstFeature` et `MyCompany.MyTechnology.SecondFeature`, peut être appelé `MyCompany.MyTechnology.dll`.</span><span class="sxs-lookup"><span data-stu-id="acfaf-109">For example, an assembly with two namespaces, `MyCompany.MyTechnology.FirstFeature` and `MyCompany.MyTechnology.SecondFeature`, could be called `MyCompany.MyTechnology.dll`.</span></span>

 <span data-ttu-id="acfaf-110">✔️ ENVISAGER de nommer les dll selon le modèle suivant :</span><span class="sxs-lookup"><span data-stu-id="acfaf-110">✔️ CONSIDER naming DLLs according to the following pattern:</span></span>

 `<Company>.<Component>.dll`

 <span data-ttu-id="acfaf-111">où `<Component>` contient une ou plusieurs clauses séparées par des points.</span><span class="sxs-lookup"><span data-stu-id="acfaf-111">where `<Component>` contains one or more dot-separated clauses.</span></span> <span data-ttu-id="acfaf-112">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="acfaf-112">For example:</span></span>

 <span data-ttu-id="acfaf-113">`Litware.Controls.dll`.</span><span class="sxs-lookup"><span data-stu-id="acfaf-113">`Litware.Controls.dll`.</span></span>

 <span data-ttu-id="acfaf-114">*Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="acfaf-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="acfaf-115">*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="acfaf-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="acfaf-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="acfaf-116">See also</span></span>

- [<span data-ttu-id="acfaf-117">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="acfaf-117">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="acfaf-118">Directives de nommage</span><span class="sxs-lookup"><span data-stu-id="acfaf-118">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
