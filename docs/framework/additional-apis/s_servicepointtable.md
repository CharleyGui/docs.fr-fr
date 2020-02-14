---
title: ServicePointManager. s_ServicePointTable Field
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
ms.openlocfilehash: 272a0c113fd70d804c763ba0e7e6e9a4a4ee04ce
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214918"
---
# <a name="servicepointmanagers_servicepointtable-field"></a><span data-ttu-id="963b5-102">ServicePointManager. s\_champ ServicePointTable</span><span class="sxs-lookup"><span data-stu-id="963b5-102">ServicePointManager.s\_ServicePointTable Field</span></span>

<span data-ttu-id="963b5-103">`ServicePointManager.s_ServicePointTable` est un <xref:System.Collections.Hashtable> qui contient la liste des connexions HTTP actives (<xref:System.Net.ServicePoint>s) dans le <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="963b5-103">`ServicePointManager.s_ServicePointTable` is a <xref:System.Collections.Hashtable> that contains the list of active HTTP connections (<xref:System.Net.ServicePoint>s) in the <xref:System.AppDomain>.</span></span>

## <a name="syntax"></a><span data-ttu-id="963b5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="963b5-104">Syntax</span></span>
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> <span data-ttu-id="963b5-105">Le champ `ServicePointManager.s_ServicePointTable` est privé et n’est pas destiné à être utilisé directement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="963b5-105">The `ServicePointManager.s_ServicePointTable` field is private and is not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="963b5-106">Microsoft ne prend pas en charge l’utilisation de ce champ dans une application de production en l’absence de toute circonstance.</span><span class="sxs-lookup"><span data-stu-id="963b5-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="963b5-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="963b5-107">Requirements</span></span>

<span data-ttu-id="963b5-108">**Espace de noms :** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="963b5-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="963b5-109">**Assembly :** Système (dans System. dll)</span><span class="sxs-lookup"><span data-stu-id="963b5-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="963b5-110">**Versions de .NET Framework :** Disponible depuis 2,0.</span><span class="sxs-lookup"><span data-stu-id="963b5-110">**.NET Framework versions:** Available since 2.0.</span></span>
