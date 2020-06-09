---
title: System.ServiceModel.Channels.ConnectionPoolCloseException
ms.date: 03/30/2017
ms.assetid: 8358898e-129e-4fac-a6bf-bf3aa4293ae2
ms.openlocfilehash: 0a312d192546655dc327667c00f4f2bbc0c15fdb
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602040"
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a><span data-ttu-id="15b02-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span><span class="sxs-lookup"><span data-stu-id="15b02-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span></span>
<span data-ttu-id="15b02-103">Une exception s'est produite en fermant les connexions dans ce pool de connexions.</span><span class="sxs-lookup"><span data-stu-id="15b02-103">An exception occurred while closing the connections in this connection pool.</span></span>  
  
## <a name="description"></a><span data-ttu-id="15b02-104">Description</span><span class="sxs-lookup"><span data-stu-id="15b02-104">Description</span></span>  
 <span data-ttu-id="15b02-105">Ce suivi de niveau d’erreur indique qu’une erreur s’est produite lors de la fermeture des pools de connexions utilisés par la fonctionnalité de regroupement de connexions de Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="15b02-105">This error level trace indicates that an error has occurred while closing the connection pools used by Windows Communication Foundation (WCF)’s connection pooling feature.</span></span> <span data-ttu-id="15b02-106">L'une des raisons possibles est l'échec de la fermeture d'une connexion en groupe, ou d'un jeu de connexions en groupe, dans CloseTimeout.</span><span class="sxs-lookup"><span data-stu-id="15b02-106">One possible reason for this is an unsuccessful closure of a pooled connection, or a set of pooled connections within the CloseTimeout.</span></span> <span data-ttu-id="15b02-107">Lorsque cette exception est levée, toutes les connexions ouvertes restantes dans ce pool sont abandonnées ; les connexions ouvertes dans d'autres pools sont abandonnées.</span><span class="sxs-lookup"><span data-stu-id="15b02-107">When this exception is thrown, any remaining unclosed connections within that pool are aborted; unclosed connections within other pools are abandoned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15b02-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="15b02-108">See also</span></span>

- [<span data-ttu-id="15b02-109">Suivi</span><span class="sxs-lookup"><span data-stu-id="15b02-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="15b02-110">Utilisation du suivi pour résoudre les problèmes posés par votre application</span><span class="sxs-lookup"><span data-stu-id="15b02-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="15b02-111">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="15b02-111">Administration and Diagnostics</span></span>](../index.md)
