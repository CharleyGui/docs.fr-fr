---
title: System.ServiceModel.Channels.HttpChannelMessageReceiveFailed
ms.date: 03/30/2017
ms.assetid: 9eb311da-fdcc-4dd3-9d85-05b3280dfdda
ms.openlocfilehash: 97f22a01df84c39915f74fa7677e5dd18154b952
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96256220"
---
# <a name="systemservicemodelchannelshttpchannelmessagereceivefailed"></a><span data-ttu-id="43b00-102">System.ServiceModel.Channels.HttpChannelMessageReceiveFailed</span><span class="sxs-lookup"><span data-stu-id="43b00-102">System.ServiceModel.Channels.HttpChannelMessageReceiveFailed</span></span>

<span data-ttu-id="43b00-103">Échec de la réception d'un message sur un canal HTTP.</span><span class="sxs-lookup"><span data-stu-id="43b00-103">Failed to receive a message over an HTTP channel.</span></span>  
  
## <a name="description"></a><span data-ttu-id="43b00-104">Description</span><span class="sxs-lookup"><span data-stu-id="43b00-104">Description</span></span>  

 <span data-ttu-id="43b00-105">Ce suivi peut être émis comme avertissement ou erreur.</span><span class="sxs-lookup"><span data-stu-id="43b00-105">This trace can be emitted as a warning or an error.</span></span> <span data-ttu-id="43b00-106">Dans les deux cas, le suivi est émis lorsqu'un écouteur compatible est introuvable pour une demande HTTP entrante et que la demande est rejetée.</span><span class="sxs-lookup"><span data-stu-id="43b00-106">In both cases, the trace is emitted when a compatible listener is not found for an incoming HTTP request and the HTTP request is discarded.</span></span> <span data-ttu-id="43b00-107">Cela peut se produire si le verbe HTTP de la demande n'a pas été reconnu pas un écouteur HTTP ou si aucun écouteur n'écoutait sur l'adresse à laquelle la demande était destinée.</span><span class="sxs-lookup"><span data-stu-id="43b00-107">This could happen because the request’s HTTP verb was not recognized by any HTTP listener, or because no listener was listening on the address the request was targeted for.</span></span> <span data-ttu-id="43b00-108">Le suivi est émis comme avertissement en cas d'auto-hébergement et comme erreur lorsque le service est hébergé dans IIS.</span><span class="sxs-lookup"><span data-stu-id="43b00-108">The trace is emitted as a warning in the self-hosted case, and as an error when the service is hosted in IIS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43b00-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="43b00-109">See also</span></span>

- [<span data-ttu-id="43b00-110">Suivi</span><span class="sxs-lookup"><span data-stu-id="43b00-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="43b00-111">Utilisation du suivi pour résoudre les problèmes posés par votre application</span><span class="sxs-lookup"><span data-stu-id="43b00-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="43b00-112">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="43b00-112">Administration and Diagnostics</span></span>](../index.md)
