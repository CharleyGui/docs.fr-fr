---
title: ServicePointManager. s_ServicePointTable Field
description: En savoir plus sur le champ ServicePointManager. s_ServicePointTable dans .NET. Ce champ de table de hachage contient des connexions HTTP actives (ServicePoints) dans AppDomain.
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.ServicePointManager.s_ServicePointTable
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 24459679-291c-401a-9def-e42b29466fcf
ms.openlocfilehash: 9462ae10125dd37706f786a1f2cef78e62fbabcc
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989545"
---
# <a name="servicepointmanagers_servicepointtable-field"></a><span data-ttu-id="613a9-104">Champ ServicePointManager. s \_ ServicePointTable</span><span class="sxs-lookup"><span data-stu-id="613a9-104">ServicePointManager.s\_ServicePointTable Field</span></span>

<span data-ttu-id="613a9-105">`ServicePointManager.s_ServicePointTable`est un <xref:System.Collections.Hashtable> qui contient la liste des connexions http actives <xref:System.Net.ServicePoint> dans le <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="613a9-105">`ServicePointManager.s_ServicePointTable` is a <xref:System.Collections.Hashtable> that contains the list of active HTTP connections (<xref:System.Net.ServicePoint>s) in the <xref:System.AppDomain>.</span></span>

## <a name="syntax"></a><span data-ttu-id="613a9-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="613a9-106">Syntax</span></span>
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> <span data-ttu-id="613a9-107">Le `ServicePointManager.s_ServicePointTable` champ est privé et n’est pas destiné à être utilisé directement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="613a9-107">The `ServicePointManager.s_ServicePointTable` field is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="613a9-108">Microsoft ne prend pas en charge l’utilisation de ce champ dans une application de production en l’absence de toute circonstance.</span><span class="sxs-lookup"><span data-stu-id="613a9-108">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="613a9-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="613a9-109">Requirements</span></span>

<span data-ttu-id="613a9-110">**Espace de noms :** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="613a9-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="613a9-111">**Assembly :** Système (en System.dll)</span><span class="sxs-lookup"><span data-stu-id="613a9-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="613a9-112">**Versions de .NET Framework :** Disponible depuis 2,0.</span><span class="sxs-lookup"><span data-stu-id="613a9-112">**.NET Framework versions:** Available since 2.0.</span></span>
