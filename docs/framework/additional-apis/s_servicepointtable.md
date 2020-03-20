---
title: ServicePointManager.s_ServicePointTable Champ
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
ms.openlocfilehash: 6a56ecd6fc85005f5987c3c2ad0d1680ca63c398
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155810"
---
# <a name="servicepointmanagers_servicepointtable-field"></a><span data-ttu-id="f3a7c-102">ServicePointManager.s\_ServicePointTable Field (en anglais)</span><span class="sxs-lookup"><span data-stu-id="f3a7c-102">ServicePointManager.s\_ServicePointTable Field</span></span>

<span data-ttu-id="f3a7c-103">`ServicePointManager.s_ServicePointTable`est <xref:System.Collections.Hashtable> un qui contient la liste<xref:System.Net.ServicePoint>des connexions HTTP actives (s) dans le <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="f3a7c-103">`ServicePointManager.s_ServicePointTable` is a <xref:System.Collections.Hashtable> that contains the list of active HTTP connections (<xref:System.Net.ServicePoint>s) in the <xref:System.AppDomain>.</span></span>

## <a name="syntax"></a><span data-ttu-id="f3a7c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3a7c-104">Syntax</span></span>
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> <span data-ttu-id="f3a7c-105">Le `ServicePointManager.s_ServicePointTable` champ est privé et n’est pas destiné à être utilisé directement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="f3a7c-105">The `ServicePointManager.s_ServicePointTable` field is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="f3a7c-106">Microsoft ne prend en charge l’utilisation de ce champ dans une application de production en aucune circonstance.</span><span class="sxs-lookup"><span data-stu-id="f3a7c-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="f3a7c-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f3a7c-107">Requirements</span></span>

<span data-ttu-id="f3a7c-108">**Espace nom:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="f3a7c-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="f3a7c-109">**Assemblée:** Système (dans System.dll)</span><span class="sxs-lookup"><span data-stu-id="f3a7c-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="f3a7c-110">**.NET Versions du Cadre:** Disponible depuis 2.0.</span><span class="sxs-lookup"><span data-stu-id="f3a7c-110">**.NET Framework versions:** Available since 2.0.</span></span>
