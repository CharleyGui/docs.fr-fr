---
title: ServicePointManager. CloseConnectionGroups, méthode (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.ServicePointManager.CloseConnectionGroups
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: aae9a389ae35e249d43c9dc830a68ec32cf4afef
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990366"
---
# <a name="servicepointmanagercloseconnectiongroups-method"></a><span data-ttu-id="5294b-102">ServicePointManager. CloseConnectionGroups, méthode</span><span class="sxs-lookup"><span data-stu-id="5294b-102">ServicePointManager.CloseConnectionGroups method</span></span>

<span data-ttu-id="5294b-103">Itère au sein de tous les points de service et ferme les groupes de connexions portant le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="5294b-103">Iterates through all service points and closes connection groups that have the specified name.</span></span>

```csharp
internal static void CloseConnectionGroups(string connectionGroupName)
```

> [!WARNING]
> <span data-ttu-id="5294b-104">Cette méthode est interne et n’est pas destinée à être utilisée directement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="5294b-104">This method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="5294b-105">Microsoft ne prend pas en charge l’utilisation de cette méthode dans une application de production en l’absence de toute circonstance.</span><span class="sxs-lookup"><span data-stu-id="5294b-105">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="parameters"></a><span data-ttu-id="5294b-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5294b-106">Parameters</span></span>

<span data-ttu-id="5294b-107">`connectionGroupName` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="5294b-107">`connectionGroupName` <xref:System.String></span></span>

<span data-ttu-id="5294b-108">Nom du groupe de connexions à fermer.</span><span class="sxs-lookup"><span data-stu-id="5294b-108">The name of the connection group to close.</span></span>

## <a name="requirements"></a><span data-ttu-id="5294b-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="5294b-109">Requirements</span></span>

<span data-ttu-id="5294b-110">**Espace de noms :** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="5294b-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="5294b-111">**Assembly :** Système (en System.dll)</span><span class="sxs-lookup"><span data-stu-id="5294b-111">**Assembly:** System (in System.dll)</span></span>
