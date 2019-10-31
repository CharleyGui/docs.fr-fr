---
title: ServicePointManager. s_ServicePointTable, champ
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 68445f4a290b9f4fe2696e35cda391b6c0ee8f85
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120003"
---
# <a name="servicepointmanagers_servicepointtable-field"></a><span data-ttu-id="9d99a-102">ServicePointManager. s\_champ ServicePointTable</span><span class="sxs-lookup"><span data-stu-id="9d99a-102">ServicePointManager.s\_ServicePointTable Field</span></span>

<span data-ttu-id="9d99a-103">`ServicePointManager.s_ServicePointTable` est un <xref:System.Collections.Hashtable> qui contient la liste des connexions HTTP actives (<xref:System.Net.ServicePoint>s) dans le <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="9d99a-103">`ServicePointManager.s_ServicePointTable` is a <xref:System.Collections.Hashtable> that contains the list of active HTTP connections (<xref:System.Net.ServicePoint>s) in the <xref:System.AppDomain>.</span></span>

## <a name="syntax"></a><span data-ttu-id="9d99a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d99a-104">Syntax</span></span>
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> <span data-ttu-id="9d99a-105">Le champ `ServicePointManager.s_ServicePointTable` est privé et n’est pas destiné à être utilisé directement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="9d99a-105">The `ServicePointManager.s_ServicePointTable` field is private and is not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="9d99a-106">Microsoft ne prend pas en charge l’utilisation de ce champ dans une application de production en l’absence de toute circonstance.</span><span class="sxs-lookup"><span data-stu-id="9d99a-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="9d99a-107">spécifications</span><span class="sxs-lookup"><span data-stu-id="9d99a-107">Requirements</span></span>

<span data-ttu-id="9d99a-108">**Espace de noms :** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="9d99a-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="9d99a-109">**Assembly :** Système (dans System. dll)</span><span class="sxs-lookup"><span data-stu-id="9d99a-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="9d99a-110">**Versions de .NET Framework :** Disponible depuis 2,0.</span><span class="sxs-lookup"><span data-stu-id="9d99a-110">**.NET Framework versions:** Available since 2.0.</span></span>
