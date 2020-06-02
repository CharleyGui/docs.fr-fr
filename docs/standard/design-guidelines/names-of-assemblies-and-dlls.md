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
ms.openlocfilehash: 138ae8154b0d10fb813f0c98ceb7c58a2471b780
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291953"
---
# <a name="names-of-assemblies-and-dlls"></a><span data-ttu-id="b8751-102">Noms d'assemblys et de DLL</span><span class="sxs-lookup"><span data-stu-id="b8751-102">Names of Assemblies and DLLs</span></span>
<span data-ttu-id="b8751-103">Un assembly est l’unité de déploiement et d’identité des programmes de code managé.</span><span class="sxs-lookup"><span data-stu-id="b8751-103">An assembly is the unit of deployment and identity for managed code programs.</span></span> <span data-ttu-id="b8751-104">Bien que les assemblys puissent couvrir un ou plusieurs fichiers, en général un assembly mappe un à un avec une DLL.</span><span class="sxs-lookup"><span data-stu-id="b8751-104">Although assemblies can span one or more files, typically an assembly maps one-to-one with a DLL.</span></span> <span data-ttu-id="b8751-105">Par conséquent, cette section décrit uniquement les conventions d’affectation de noms de DLL, qui peuvent alors être mappées aux conventions d’affectation de noms d’assembly.</span><span class="sxs-lookup"><span data-stu-id="b8751-105">Therefore, this section describes only DLL naming conventions, which then can be mapped to assembly naming conventions.</span></span>

 <span data-ttu-id="b8751-106">✔️ Choisissez des noms pour vos dll d’assembly qui suggèrent de grands blocs de fonctionnalités, tels que System. Data.</span><span class="sxs-lookup"><span data-stu-id="b8751-106">✔️ DO choose names for your assembly DLLs that suggest large chunks of functionality, such as System.Data.</span></span>

 <span data-ttu-id="b8751-107">Les noms d’assemblys et de DLL ne doivent pas nécessairement correspondre aux noms d’espaces de noms, mais il est raisonnable de suivre le nom de l’espace de noms lors de l’attribution de noms aux assemblys.</span><span class="sxs-lookup"><span data-stu-id="b8751-107">Assembly and DLL names don’t have to correspond to namespace names, but it is reasonable to follow the namespace name when naming assemblies.</span></span> <span data-ttu-id="b8751-108">Une bonne règle empirique consiste à nommer la DLL en fonction du préfixe commun des espaces de noms contenus dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="b8751-108">A good rule of thumb is to name the DLL based on the common prefix of the namespaces contained in the assembly.</span></span> <span data-ttu-id="b8751-109">Par exemple, un assembly avec deux espaces de noms, `MyCompany.MyTechnology.FirstFeature` et `MyCompany.MyTechnology.SecondFeature` , peut être appelé `MyCompany.MyTechnology.dll` .</span><span class="sxs-lookup"><span data-stu-id="b8751-109">For example, an assembly with two namespaces, `MyCompany.MyTechnology.FirstFeature` and `MyCompany.MyTechnology.SecondFeature`, could be called `MyCompany.MyTechnology.dll`.</span></span>

 <span data-ttu-id="b8751-110">✔️ ENVISAGER de nommer les dll selon le modèle suivant :</span><span class="sxs-lookup"><span data-stu-id="b8751-110">✔️ CONSIDER naming DLLs according to the following pattern:</span></span>

 `<Company>.<Component>.dll`

 <span data-ttu-id="b8751-111">où `<Component>` contient une ou plusieurs clauses séparées par des points.</span><span class="sxs-lookup"><span data-stu-id="b8751-111">where `<Component>` contains one or more dot-separated clauses.</span></span> <span data-ttu-id="b8751-112">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="b8751-112">For example:</span></span>

 <span data-ttu-id="b8751-113">`Litware.Controls.dll`.</span><span class="sxs-lookup"><span data-stu-id="b8751-113">`Litware.Controls.dll`.</span></span>

 <span data-ttu-id="b8751-114">*Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="b8751-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="b8751-115">*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="b8751-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="b8751-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b8751-116">See also</span></span>

- [<span data-ttu-id="b8751-117">Directives de conception d’infrastructure</span><span class="sxs-lookup"><span data-stu-id="b8751-117">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="b8751-118">Instructions d’affectation de noms</span><span class="sxs-lookup"><span data-stu-id="b8751-118">Naming Guidelines</span></span>](naming-guidelines.md)
