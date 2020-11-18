---
title: Instructions de conception pour les exceptions
ms.date: 10/22/2008
helpviewer_keywords:
- exceptions [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], exceptions
- errors [.NET Framework], exceptions
- reporting errors
ms.assetid: bc177b2f-7528-4ae4-83db-aacfb04b86d0
ms.openlocfilehash: 776e559bb1629245c275cb4463531a8dd4b230ae
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821149"
---
# <a name="design-guidelines-for-exceptions"></a><span data-ttu-id="987e9-102">Instructions de conception pour les exceptions</span><span class="sxs-lookup"><span data-stu-id="987e9-102">Design Guidelines for Exceptions</span></span>
<span data-ttu-id="987e9-103">La gestion des exceptions présente de nombreux avantages par rapport aux rapports d’erreurs basés sur les valeurs de retour.</span><span class="sxs-lookup"><span data-stu-id="987e9-103">Exception handling has many advantages over return-value-based error reporting.</span></span> <span data-ttu-id="987e9-104">Une bonne conception d’infrastructure aide le développeur d’applications à tirer parti des avantages des exceptions.</span><span class="sxs-lookup"><span data-stu-id="987e9-104">Good framework design helps the application developer realize the benefits of exceptions.</span></span> <span data-ttu-id="987e9-105">Cette section présente les avantages des exceptions et présente les instructions permettant de les utiliser efficacement.</span><span class="sxs-lookup"><span data-stu-id="987e9-105">This section discusses the benefits of exceptions and presents guidelines for using them effectively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="987e9-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="987e9-106">In This Section</span></span>  
 [<span data-ttu-id="987e9-107">Levée d’exception</span><span class="sxs-lookup"><span data-stu-id="987e9-107">Exception Throwing</span></span>](exception-throwing.md)  
 [<span data-ttu-id="987e9-108">Utilisation de types d'exceptions standard</span><span class="sxs-lookup"><span data-stu-id="987e9-108">Using Standard Exception Types</span></span>](using-standard-exception-types.md)  
 [<span data-ttu-id="987e9-109">Exceptions et performances</span><span class="sxs-lookup"><span data-stu-id="987e9-109">Exceptions and Performance</span></span>](exceptions-and-performance.md)  
 <span data-ttu-id="987e9-110">*Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="987e9-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="987e9-111">*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="987e9-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="987e9-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="987e9-112">See also</span></span>

- [<span data-ttu-id="987e9-113">Directives de conception d’infrastructure</span><span class="sxs-lookup"><span data-stu-id="987e9-113">Framework Design Guidelines</span></span>](index.md)
