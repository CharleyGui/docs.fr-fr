---
title: Un appel à une propriété ou une méthode ne peut pas utiliser une référence vers un objet privé, que ce soit comme argument ou comme valeur de retour
ms.date: 07/20/2015
f1_keywords:
- vbrID98
ms.assetid: 059b43e1-202d-4fa2-806b-7bad63c1e7ca
ms.openlocfilehash: 53f9052555555a5b9dcb038dfee9cd54dc2b4251
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976202"
---
# <a name="a-property-or-method-call-cannot-include-a-reference-to-a-private-object-either-as-an-argument-or-as-a-return-value"></a><span data-ttu-id="ef8c6-102">Un appel à une propriété ou une méthode ne peut pas utiliser une référence vers un objet privé, que ce soit comme argument ou comme valeur de retour</span><span class="sxs-lookup"><span data-stu-id="ef8c6-102">A property or method call cannot include a reference to a private object, either as an argument or as a return value</span></span>

<span data-ttu-id="ef8c6-103">Cette erreur peut avoir plusieurs causes, dont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="ef8c6-103">Among the possible causes of this error are:</span></span>  
  
- <span data-ttu-id="ef8c6-104">Un client a appelé une propriété ou méthode d’un composant hors processus et a tenté de passer une référence à un objet privé comme l’un des arguments.</span><span class="sxs-lookup"><span data-stu-id="ef8c6-104">A client invoked a property or method of an out-of-process component and attempted to pass a reference to a private object as one of the arguments.</span></span>  
  
- <span data-ttu-id="ef8c6-105">Un composant hors processus a appelé une méthode de rappel sur son client et a tenté de passer une référence à un objet privé.</span><span class="sxs-lookup"><span data-stu-id="ef8c6-105">An out-of-process component invoked a call-back method on its client and attempted to pass a reference to a private object.</span></span>  
  
- <span data-ttu-id="ef8c6-106">Un composant hors processus a tenté de passer une référence à un objet privé comme argument d’un événement qu’il a déclenché.</span><span class="sxs-lookup"><span data-stu-id="ef8c6-106">An out-of-process component attempted to pass a reference to a private object as an argument of an event it was raising.</span></span>  
  
- <span data-ttu-id="ef8c6-107">Un client a tenté d’assigner une référence d’objet privé à un argument `ByRef` d’un événement qu’il gérait.</span><span class="sxs-lookup"><span data-stu-id="ef8c6-107">A client attempted to assign a private object reference to a `ByRef` argument of an event it was handling.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ef8c6-108">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="ef8c6-108">To correct this error</span></span>  
  
1. <span data-ttu-id="ef8c6-109">Supprimez la référence.</span><span class="sxs-lookup"><span data-stu-id="ef8c6-109">Remove the reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef8c6-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ef8c6-110">See also</span></span>

- [<span data-ttu-id="ef8c6-111">Private</span><span class="sxs-lookup"><span data-stu-id="ef8c6-111">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
