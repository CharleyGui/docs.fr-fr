---
title: Sécurisation des données d'état
description: Déclarez les données d’État comme des variables privées ou internes pour limiter l’accès à celle-ci. Ces données sont toujours accessibles via la réflexion, la sérialisation et le débogage.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET], state data
- code security, state data
- secure coding, state data
- state data security
ms.assetid: 12671309-2877-43fe-a3df-6863507e712d
ms.openlocfilehash: 73bd0ace28e5b9661cc86d6749ceef9aa4c9ac92
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87557123"
---
# <a name="securing-state-data"></a><span data-ttu-id="04e02-104">Sécurisation des données d'état</span><span class="sxs-lookup"><span data-stu-id="04e02-104">Securing State Data</span></span>

<span data-ttu-id="04e02-105">Les applications qui gèrent des données sensibles ou participent aux processus décisionnels de sécurité doivent conserver le contrôle des données. Elles doivent absolument empêcher tout code potentiellement malveillant d’accéder directement aux données.</span><span class="sxs-lookup"><span data-stu-id="04e02-105">Applications that handle sensitive data or make any kind of security decisions need to keep that data under their own control and cannot allow other potentially malicious code to access the data directly.</span></span> <span data-ttu-id="04e02-106">La meilleure façon de protéger les données en mémoire est de les déclarer en tant que variables privées ou internes (avec une portée limitée au même assembly).</span><span class="sxs-lookup"><span data-stu-id="04e02-106">The best way to protect data in memory is to declare the data as private or internal (with scope limited to the same assembly) variables.</span></span> <span data-ttu-id="04e02-107">Toutefois, même ces données sont soumises à un accès dont vous devez avoir conscience :</span><span class="sxs-lookup"><span data-stu-id="04e02-107">However, even this data is subject to access you should be aware of:</span></span>  
  
- <span data-ttu-id="04e02-108">À l’aide de mécanismes de réflexion, du code hautement fiable pouvant référencer votre objet est susceptible d’obtenir et de définir des membres privés.</span><span class="sxs-lookup"><span data-stu-id="04e02-108">Using reflection mechanisms, highly trusted code that can reference your object can get and set private members.</span></span>  
  
- <span data-ttu-id="04e02-109">En s’appuyant sur la sérialisation, le code hautement fiable peut efficacement obtenir et définir des membres privés, s’il peut accéder aux données correspondantes de la forme sérialisée de l’objet.</span><span class="sxs-lookup"><span data-stu-id="04e02-109">Using serialization, highly trusted code can effectively get and set private members if it can access the corresponding data in the serialized form of the object.</span></span>  
  
- <span data-ttu-id="04e02-110">En mode de débogage, ces données peuvent être lues.</span><span class="sxs-lookup"><span data-stu-id="04e02-110">Under debugging, this data can be read.</span></span>  
  
 <span data-ttu-id="04e02-111">Assurez-vous qu’aucune de vos méthodes ou propriétés n’expose involontairement ces valeurs.</span><span class="sxs-lookup"><span data-stu-id="04e02-111">Make sure none of your own methods or properties exposes these values unintentionally.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04e02-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="04e02-112">See also</span></span>

- [<span data-ttu-id="04e02-113">Instructions de codage sécurisé</span><span class="sxs-lookup"><span data-stu-id="04e02-113">Secure Coding Guidelines</span></span>](secure-coding-guidelines.md)
- [<span data-ttu-id="04e02-114">Sécurité ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="04e02-114">ASP.NET Core Security</span></span>](/aspnet/core/security/)
