---
title: 4208 - RetryingSqlCommandDueToSqlError
ms.date: 03/30/2017
ms.assetid: a8e6483a-a6e4-4bbf-82ec-cd8b6e711aad
ms.openlocfilehash: 088754cb15c2e55faa1d43a1da1c79ddcddd69f1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96280414"
---
# <a name="4208---retryingsqlcommandduetosqlerror"></a><span data-ttu-id="e1937-102">4208 - RetryingSqlCommandDueToSqlError</span><span class="sxs-lookup"><span data-stu-id="e1937-102">4208 - RetryingSqlCommandDueToSqlError</span></span>

## <a name="properties"></a><span data-ttu-id="e1937-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="e1937-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e1937-104">id</span><span class="sxs-lookup"><span data-stu-id="e1937-104">ID</span></span>|<span data-ttu-id="e1937-105">4208</span><span class="sxs-lookup"><span data-stu-id="e1937-105">4208</span></span>|  
|<span data-ttu-id="e1937-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="e1937-106">Keywords</span></span>|<span data-ttu-id="e1937-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="e1937-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="e1937-108">Level</span><span class="sxs-lookup"><span data-stu-id="e1937-108">Level</span></span>|<span data-ttu-id="e1937-109">Informations</span><span class="sxs-lookup"><span data-stu-id="e1937-109">Information</span></span>|  
|<span data-ttu-id="e1937-110">Channel</span><span class="sxs-lookup"><span data-stu-id="e1937-110">Channel</span></span>|<span data-ttu-id="e1937-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="e1937-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e1937-112">Description</span><span class="sxs-lookup"><span data-stu-id="e1937-112">Description</span></span>  

 <span data-ttu-id="e1937-113">Indique que le fournisseur SQL effectue une nouvelle tentative de commande SQL en raison d'une erreur SQL.</span><span class="sxs-lookup"><span data-stu-id="e1937-113">Indicates the SQL provider is retrying a SQL command due to a SQL error.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e1937-114">Message</span><span class="sxs-lookup"><span data-stu-id="e1937-114">Message</span></span>  

 <span data-ttu-id="e1937-115">Nouvelle tentative d'exécution d'une commande SQL en raison du numéro d'erreur SQL %1.</span><span class="sxs-lookup"><span data-stu-id="e1937-115">Retrying a SQL command due to SQL error number %1.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e1937-116">Détails</span><span class="sxs-lookup"><span data-stu-id="e1937-116">Details</span></span>  
  
|<span data-ttu-id="e1937-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="e1937-117">Data Item Name</span></span>|<span data-ttu-id="e1937-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="e1937-118">Data Item Type</span></span>|<span data-ttu-id="e1937-119">Description</span><span class="sxs-lookup"><span data-stu-id="e1937-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e1937-120">ErrorNumber</span><span class="sxs-lookup"><span data-stu-id="e1937-120">ErrorNumber</span></span>|<span data-ttu-id="e1937-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="e1937-121">xs:string</span></span>|<span data-ttu-id="e1937-122">Numéro d'erreur SQL.</span><span class="sxs-lookup"><span data-stu-id="e1937-122">The SQL error number.</span></span>|  
|<span data-ttu-id="e1937-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e1937-123">AppDomain</span></span>|<span data-ttu-id="e1937-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="e1937-124">xs:string</span></span>|<span data-ttu-id="e1937-125">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e1937-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
