---
title: Coclasse ComCallUnmarshal
ms.date: 03/30/2017
api_name:
- ComCallUnmarshal Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ComCallUnmarshal
helpviewer_keywords:
- ComCallUnmarshal coclass [.NET Framework hosting]
ms.assetid: 2adb5827-2268-4914-a1c6-f62b61880a45
topic_type:
- apiref
ms.openlocfilehash: 939acc0ad47021d5fdffe7b7b71ea6a4a1635a6d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616734"
---
# <a name="comcallunmarshal-coclass"></a><span data-ttu-id="074a3-102">Coclasse ComCallUnmarshal</span><span class="sxs-lookup"><span data-stu-id="074a3-102">ComCallUnmarshal Coclass</span></span>
<span data-ttu-id="074a3-103">Fournit des interfaces pour gérer le marshaling des pointeurs d’interface.</span><span class="sxs-lookup"><span data-stu-id="074a3-103">Provides interfaces for managing the marshaling of interface pointers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="074a3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="074a3-104">Syntax</span></span>  
  
```cpp  
coclass ComCallUnmarshal {  
    [default] interface IMarshal;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="074a3-105">Interfaces</span><span class="sxs-lookup"><span data-stu-id="074a3-105">Interfaces</span></span>  
  
|<span data-ttu-id="074a3-106">Interface</span><span class="sxs-lookup"><span data-stu-id="074a3-106">Interface</span></span>|<span data-ttu-id="074a3-107">Description</span><span class="sxs-lookup"><span data-stu-id="074a3-107">Description</span></span>|  
|---------------|-----------------|  
|`IMarshal`|<span data-ttu-id="074a3-108">Fournit des méthodes pour créer, initialiser et gérer un proxy dans un processus client.</span><span class="sxs-lookup"><span data-stu-id="074a3-108">Provides methods for creating, initializing, and managing a proxy in a client process.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="074a3-109">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="074a3-109">Requirements</span></span>  
 <span data-ttu-id="074a3-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="074a3-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="074a3-111">**En-tête :** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="074a3-111">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="074a3-112">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="074a3-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="074a3-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="074a3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="074a3-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="074a3-114">See also</span></span>

- [<span data-ttu-id="074a3-115">Hébergement des coclasses</span><span class="sxs-lookup"><span data-stu-id="074a3-115">Hosting Coclasses</span></span>](hosting-coclasses.md)
