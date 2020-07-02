---
ms.openlocfilehash: b521f4163bf5bf4a369d0eec12dae503703a976e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614435"
---
### <a name="throttle-concurrent-requests-per-session"></a><span data-ttu-id="17141-101">Restriction des demandes simultanées par session</span><span class="sxs-lookup"><span data-stu-id="17141-101">Throttle concurrent requests per session</span></span>

#### <a name="details"></a><span data-ttu-id="17141-102">Détails</span><span class="sxs-lookup"><span data-stu-id="17141-102">Details</span></span>

<span data-ttu-id="17141-103">Dans .NET Framework 4.6.2 et les versions antérieures, ASP.NET exécute les requêtes séquentiellement avec le même SessionId et émet toujours SessionId par le biais de cookies par défaut.</span><span class="sxs-lookup"><span data-stu-id="17141-103">In the .NET Framework 4.6.2 and earlier, ASP.NET executes requests with the same Sessionid sequentially, and ASP.NET always issues the Sessionid through cookies by default.</span></span> <span data-ttu-id="17141-104">Si la réponse d’une page prend beaucoup de temps, cela réduit considérablement les performances du serveur simplement en appuyant sur <kbd>F5</kbd> sur le navigateur.</span><span class="sxs-lookup"><span data-stu-id="17141-104">If a page takes a long time to respond, it will significantly degrade server performance just by pressing <kbd>F5</kbd> on the browser.</span></span> <span data-ttu-id="17141-105">Dans le correctif, nous avons ajouté un compteur pour effectuer le suivi des requêtes en file d’attente et arrêter les requêtes quand elles dépassent une limite spécifiée.</span><span class="sxs-lookup"><span data-stu-id="17141-105">In the fix, we added a counter to track the queued requests and terminate the requests when they exceed a specified limit.</span></span> <span data-ttu-id="17141-106">La valeur par défaut est 50.</span><span class="sxs-lookup"><span data-stu-id="17141-106">The default value is 50.</span></span> <span data-ttu-id="17141-107">Si la limite est atteinte, un avertissement est journalisé dans le journal des événements et une réponse HTTP 500 peut être enregistrée dans le journal IIS.</span><span class="sxs-lookup"><span data-stu-id="17141-107">If the limit is reached, a warning will be logged in the event log, and an HTTP 500 response may be recorded in the IIS log.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="17141-108">Suggestion</span><span class="sxs-lookup"><span data-stu-id="17141-108">Suggestion</span></span>

<span data-ttu-id="17141-109">Pour restaurer l’ancien comportement, vous pouvez ajouter le paramètre suivant à votre fichier web.config pour désactiver le nouveau comportement.</span><span class="sxs-lookup"><span data-stu-id="17141-109">To restore the old behavior, you can add the following setting to your web.config file to opt out of the new behavior.</span></span>

```xml
<appSettings>
    <add key="aspnet:RequestQueueLimitPerSession" value="2147483647"/>
</appSettings>
```

| <span data-ttu-id="17141-110">Nom</span><span class="sxs-lookup"><span data-stu-id="17141-110">Name</span></span>    | <span data-ttu-id="17141-111">Valeur</span><span class="sxs-lookup"><span data-stu-id="17141-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="17141-112">Étendue</span><span class="sxs-lookup"><span data-stu-id="17141-112">Scope</span></span>   | <span data-ttu-id="17141-113">Edge</span><span class="sxs-lookup"><span data-stu-id="17141-113">Edge</span></span>        |
| <span data-ttu-id="17141-114">Version</span><span class="sxs-lookup"><span data-stu-id="17141-114">Version</span></span> | <span data-ttu-id="17141-115">4,7</span><span class="sxs-lookup"><span data-stu-id="17141-115">4.7</span></span>         |
| <span data-ttu-id="17141-116">Type</span><span class="sxs-lookup"><span data-stu-id="17141-116">Type</span></span>    | <span data-ttu-id="17141-117">Reciblage</span><span class="sxs-lookup"><span data-stu-id="17141-117">Retargeting</span></span> |
