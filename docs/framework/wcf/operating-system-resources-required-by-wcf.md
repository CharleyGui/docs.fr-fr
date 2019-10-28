---
title: Ressources de système d'exploitation requises par WCF
ms.date: 03/30/2017
ms.assetid: cdd9a331-53fe-4e0d-bdfe-782264aec5c9
ms.openlocfilehash: c2c26d769424a8d0655591cb10b4b13df8a15884
ms.sourcegitcommit: 9b2ef64c4fc10a4a10f28a223d60d17d7d249ee8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/26/2019
ms.locfileid: "72961137"
---
# <a name="operating-system-resources-required-by-wcf"></a><span data-ttu-id="74472-102">Ressources de système d'exploitation requises par WCF</span><span class="sxs-lookup"><span data-stu-id="74472-102">Operating System Resources Required by WCF</span></span>

<span data-ttu-id="74472-103">Windows Communication Foundation (WCF) dépend de plusieurs ressources fournies par le système d’exploitation pour fonctionner.</span><span class="sxs-lookup"><span data-stu-id="74472-103">Windows Communication Foundation (WCF) depends on several resources that are provided by the operating system to function.</span></span> <span data-ttu-id="74472-104">Le tableau suivant répertorie ces ressources :</span><span class="sxs-lookup"><span data-stu-id="74472-104">The following table lists those resources:</span></span>

|<span data-ttu-id="74472-105">Ressource</span><span class="sxs-lookup"><span data-stu-id="74472-105">Resource</span></span>|<span data-ttu-id="74472-106">Description</span><span class="sxs-lookup"><span data-stu-id="74472-106">Description</span></span>|
|--------------|-----------------|
|<span data-ttu-id="74472-107">Microsoft Distributed Transaction Coordinator (MSDTC)</span><span class="sxs-lookup"><span data-stu-id="74472-107">Microsoft Distributed Transaction Coordinator (MSDTC)</span></span>|<span data-ttu-id="74472-108">Requis pour prendre en charge les transactions OleTx.</span><span class="sxs-lookup"><span data-stu-id="74472-108">Required to support OleTx transactions.</span></span>|
|<span data-ttu-id="74472-109">Services IIS (Internet Information Services)</span><span class="sxs-lookup"><span data-stu-id="74472-109">Internet Information Services (IIS)</span></span>|<span data-ttu-id="74472-110">Requis si vous souhaitez utiliser les services Internet (IIS) pour héberger votre application.</span><span class="sxs-lookup"><span data-stu-id="74472-110">Required if you want to use IIS to host your application.</span></span>|
|<span data-ttu-id="74472-111">Windows Process Activation Service (WAS)</span><span class="sxs-lookup"><span data-stu-id="74472-111">Windows Process Activation Service (WAS)</span></span>|<span data-ttu-id="74472-112">Requis si vous souhaitez utiliser les services WAS pour héberger votre application.</span><span class="sxs-lookup"><span data-stu-id="74472-112">Required if you want to use WAS to host your application.</span></span>|
