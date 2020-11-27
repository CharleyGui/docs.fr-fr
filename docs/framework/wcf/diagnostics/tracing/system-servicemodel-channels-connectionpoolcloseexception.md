---
title: System.ServiceModel.Channels.ConnectionPoolCloseException
ms.date: 03/30/2017
ms.assetid: 8358898e-129e-4fac-a6bf-bf3aa4293ae2
ms.openlocfilehash: d8edb8e916578247e62e3a3eb3b11b80f93416cd
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96286953"
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a><span data-ttu-id="0676c-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span><span class="sxs-lookup"><span data-stu-id="0676c-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span></span>

<span data-ttu-id="0676c-103">Une exception s'est produite en fermant les connexions dans ce pool de connexions.</span><span class="sxs-lookup"><span data-stu-id="0676c-103">An exception occurred while closing the connections in this connection pool.</span></span>  
  
## <a name="description"></a><span data-ttu-id="0676c-104">Description</span><span class="sxs-lookup"><span data-stu-id="0676c-104">Description</span></span>  

 <span data-ttu-id="0676c-105">Ce suivi de niveau d’erreur indique qu’une erreur s’est produite lors de la fermeture des pools de connexions utilisés par la fonctionnalité de regroupement de connexions de Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="0676c-105">This error level trace indicates that an error has occurred while closing the connection pools used by Windows Communication Foundation (WCF)’s connection pooling feature.</span></span> <span data-ttu-id="0676c-106">L'une des raisons possibles est l'échec de la fermeture d'une connexion en groupe, ou d'un jeu de connexions en groupe, dans CloseTimeout.</span><span class="sxs-lookup"><span data-stu-id="0676c-106">One possible reason for this is an unsuccessful closure of a pooled connection, or a set of pooled connections within the CloseTimeout.</span></span> <span data-ttu-id="0676c-107">Lorsque cette exception est levée, toutes les connexions ouvertes restantes dans ce pool sont abandonnées ; les connexions ouvertes dans d'autres pools sont abandonnées.</span><span class="sxs-lookup"><span data-stu-id="0676c-107">When this exception is thrown, any remaining unclosed connections within that pool are aborted; unclosed connections within other pools are abandoned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0676c-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0676c-108">See also</span></span>

- [<span data-ttu-id="0676c-109">Suivi</span><span class="sxs-lookup"><span data-stu-id="0676c-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="0676c-110">Utilisation du suivi pour résoudre les problèmes posés par votre application</span><span class="sxs-lookup"><span data-stu-id="0676c-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="0676c-111">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="0676c-111">Administration and Diagnostics</span></span>](../index.md)
