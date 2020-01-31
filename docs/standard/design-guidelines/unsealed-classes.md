---
title: Classes unsealed
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- classes [.NET Framework], unsealed
- unsealed classes
- inheritance, classes
ms.assetid: 9a3bd505-90f5-4053-9f0d-3cf5fa3d3ebf
ms.openlocfilehash: 6804a79e8beee1d42e313509966b46239e66c25f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743551"
---
# <a name="unsealed-classes"></a><span data-ttu-id="23001-102">Classes unsealed</span><span class="sxs-lookup"><span data-stu-id="23001-102">Unsealed Classes</span></span>
<span data-ttu-id="23001-103">Les classes sealed ne peuvent pas être héritées de, et elles empêchent l’extensibilité.</span><span class="sxs-lookup"><span data-stu-id="23001-103">Sealed classes cannot be inherited from, and they prevent extensibility.</span></span> <span data-ttu-id="23001-104">En revanche, les classes qui peuvent être héritées de sont appelées « classes non scellées ».</span><span class="sxs-lookup"><span data-stu-id="23001-104">In contrast, classes that can be inherited from are called unsealed classes.</span></span>

 <span data-ttu-id="23001-105">✔️ envisagez d’utiliser des classes non scellées sans membres virtuels ou protégés comme un excellent moyen de fournir une extensibilité encore plus coûteuse à un Framework.</span><span class="sxs-lookup"><span data-stu-id="23001-105">✔️ CONSIDER using unsealed classes with no added virtual or protected members as a great way to provide inexpensive yet much appreciated extensibility to a framework.</span></span>

 <span data-ttu-id="23001-106">Les développeurs souhaitent souvent hériter de classes non scellées afin d’ajouter des membres de commodité tels que des constructeurs personnalisés, de nouvelles méthodes ou des surcharges de méthode.</span><span class="sxs-lookup"><span data-stu-id="23001-106">Developers often want to inherit from unsealed classes so as to add convenience members such as custom constructors, new methods, or method overloads.</span></span> <span data-ttu-id="23001-107">Par exemple, `System.Messaging.MessageQueue` est déscellée et permet ainsi aux utilisateurs de créer des files d’attente personnalisées qui se trouvent par défaut dans un chemin d’accès de file d’attente particulier ou d’ajouter des méthodes personnalisées qui simplifient l’API pour des scénarios spécifiques.</span><span class="sxs-lookup"><span data-stu-id="23001-107">For example,  `System.Messaging.MessageQueue` is unsealed and thus allows users to create custom queues that default to a particular queue path or to add custom methods that simplify the API for specific scenarios.</span></span>

 <span data-ttu-id="23001-108">Les classes sont déscellées par défaut dans la plupart des langages de programmation, et il s’agit également de la valeur par défaut recommandée pour la plupart des classes dans les infrastructures.</span><span class="sxs-lookup"><span data-stu-id="23001-108">Classes are unsealed by default in most programming languages, and this is also the recommended default for most classes in frameworks.</span></span> <span data-ttu-id="23001-109">L’extensibilité offerte par les types non scellés est grandement appréciée par les utilisateurs du Framework et très peu coûteuse à fournir en raison des coûts de test relativement faibles associés aux types non scellés.</span><span class="sxs-lookup"><span data-stu-id="23001-109">The extensibility afforded by unsealed types is much appreciated by framework users and quite inexpensive to provide because of relatively low test costs associated with unsealed types.</span></span>

 <span data-ttu-id="23001-110">*Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="23001-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="23001-111">*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="23001-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="23001-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="23001-112">See also</span></span>

- [<span data-ttu-id="23001-113">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="23001-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="23001-114">Conception en vue de l’extensibilité</span><span class="sxs-lookup"><span data-stu-id="23001-114">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
- [<span data-ttu-id="23001-115">Scellement</span><span class="sxs-lookup"><span data-stu-id="23001-115">Sealing</span></span>](../../../docs/standard/design-guidelines/sealing.md)
