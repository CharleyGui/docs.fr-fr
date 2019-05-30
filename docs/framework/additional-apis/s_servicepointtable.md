---
title: Champ de ServicePointManager.s_ServicePointTable
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
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 840d068d282e3ba35df5aee6a11ff96d9e6bfdbd
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301390"
---
# <a name="servicepointmanagersservicepointtable-field"></a><span data-ttu-id="0c402-102">ServicePointManager.s\_ServicePointTable champ</span><span class="sxs-lookup"><span data-stu-id="0c402-102">ServicePointManager.s\_ServicePointTable Field</span></span>

<span data-ttu-id="0c402-103">`ServicePointManager.s_ServicePointTable` est un <xref:System.Collections.Hashtable> qui contient la liste des connexions HTTP actives (<xref:System.Net.ServicePoint>s) dans le <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="0c402-103">`ServicePointManager.s_ServicePointTable` is a <xref:System.Collections.Hashtable> that contains the list of active HTTP connections (<xref:System.Net.ServicePoint>s) in the <xref:System.AppDomain>.</span></span>

## <a name="syntax"></a><span data-ttu-id="0c402-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0c402-104">Syntax</span></span>
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> <span data-ttu-id="0c402-105">Le `ServicePointManager.s_ServicePointTable` champ est privé et n’est pas destiné à être utilisé directement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="0c402-105">The `ServicePointManager.s_ServicePointTable` field is private and is not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="0c402-106">Microsoft ne prend pas en charge l’utilisation de ce champ dans une application de production en toute circonstance.</span><span class="sxs-lookup"><span data-stu-id="0c402-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="0c402-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0c402-107">Requirements</span></span>

<span data-ttu-id="0c402-108">**Espace de noms :** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="0c402-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="0c402-109">**Assembly :** Système (dans System.dll)</span><span class="sxs-lookup"><span data-stu-id="0c402-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="0c402-110">**Versions du .NET framework :** Disponible à partir de 2.0.</span><span class="sxs-lookup"><span data-stu-id="0c402-110">**.NET Framework versions:** Available since 2.0.</span></span>
