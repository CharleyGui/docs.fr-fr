---
title: Sécurisation des données d'état
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET Framework], state data
- code security, state data
- secure coding, state data
- state data security
ms.assetid: 12671309-2877-43fe-a3df-6863507e712d
ms.openlocfilehash: c30bd2fe9e1ed371be2db60739d3b329fea788c7
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705897"
---
# <a name="securing-state-data"></a><span data-ttu-id="0961a-102">Sécurisation des données d'état</span><span class="sxs-lookup"><span data-stu-id="0961a-102">Securing State Data</span></span>
<span data-ttu-id="0961a-103">Les applications qui gèrent des données sensibles ou participent aux processus décisionnels de sécurité doivent conserver le contrôle des données. Elles doivent absolument empêcher tout code potentiellement malveillant d’accéder directement aux données.</span><span class="sxs-lookup"><span data-stu-id="0961a-103">Applications that handle sensitive data or make any kind of security decisions need to keep that data under their own control and cannot allow other potentially malicious code to access the data directly.</span></span> <span data-ttu-id="0961a-104">La meilleure façon de protéger les données en mémoire est de les déclarer en tant que variables privées ou internes (avec une portée limitée au même assembly).</span><span class="sxs-lookup"><span data-stu-id="0961a-104">The best way to protect data in memory is to declare the data as private or internal (with scope limited to the same assembly) variables.</span></span> <span data-ttu-id="0961a-105">Toutefois, même ces données sont soumises à un accès dont vous devez avoir conscience :</span><span class="sxs-lookup"><span data-stu-id="0961a-105">However, even this data is subject to access you should be aware of:</span></span>  
  
- <span data-ttu-id="0961a-106">À l’aide de mécanismes de réflexion, du code hautement fiable pouvant référencer votre objet est susceptible d’obtenir et de définir des membres privés.</span><span class="sxs-lookup"><span data-stu-id="0961a-106">Using reflection mechanisms, highly trusted code that can reference your object can get and set private members.</span></span>  
  
- <span data-ttu-id="0961a-107">En s’appuyant sur la sérialisation, le code hautement fiable peut efficacement obtenir et définir des membres privés, s’il peut accéder aux données correspondantes de la forme sérialisée de l’objet.</span><span class="sxs-lookup"><span data-stu-id="0961a-107">Using serialization, highly trusted code can effectively get and set private members if it can access the corresponding data in the serialized form of the object.</span></span>  
  
- <span data-ttu-id="0961a-108">En mode de débogage, ces données peuvent être lues.</span><span class="sxs-lookup"><span data-stu-id="0961a-108">Under debugging, this data can be read.</span></span>  
  
 <span data-ttu-id="0961a-109">Assurez-vous qu’aucune de vos méthodes ou propriétés n’expose involontairement ces valeurs.</span><span class="sxs-lookup"><span data-stu-id="0961a-109">Make sure none of your own methods or properties exposes these values unintentionally.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0961a-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0961a-110">See also</span></span>

- [<span data-ttu-id="0961a-111">Instructions de codage sécurisé</span><span class="sxs-lookup"><span data-stu-id="0961a-111">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
