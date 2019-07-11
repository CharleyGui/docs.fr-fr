---
title: IInstallReferenceEnum, interface
ms.date: 03/30/2017
api_name:
- IInstallReferenceEnum
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IInstallReferenceEnum
helpviewer_keywords:
- IInstallReferenceEnum interface [.NET Framework fusion]
ms.assetid: 2863b33b-a541-462c-bbe8-702a2832898e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5781254b508887f2e76f6ca0eca6a2830ada172b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774015"
---
# <a name="iinstallreferenceenum-interface"></a><span data-ttu-id="eb82c-102">IInstallReferenceEnum, interface</span><span class="sxs-lookup"><span data-stu-id="eb82c-102">IInstallReferenceEnum Interface</span></span>
<span data-ttu-id="eb82c-103">Représente un énumérateur pour les assemblys référencés installés dans le global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="eb82c-103">Represents an enumerator for the referenced assemblies installed in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb82c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eb82c-104">Syntax</span></span>  
  
```cpp  
interface IInstallReferenceEnum : IUnknown {  
    HRESULT GetNextInstallReferenceItem (  
        [out] IInstallReferenceItem **ppRefItem,  
        [in]  DWORD dwFlags,  
        [in]  LPVOID pvReserved  
    );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="eb82c-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="eb82c-105">Methods</span></span>  
  
|<span data-ttu-id="eb82c-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="eb82c-106">Method</span></span>|<span data-ttu-id="eb82c-107">Description</span><span class="sxs-lookup"><span data-stu-id="eb82c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eb82c-108">GetNextInstallReferenceItem, méthode</span><span class="sxs-lookup"><span data-stu-id="eb82c-108">GetNextInstallReferenceItem Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-getnextinstallreferenceitem-method.md)|<span data-ttu-id="eb82c-109">Obtient un pointeur vers la prochaine `IInstallReferenceItem` contenues dans cette `IInstallReferenceEnum`.</span><span class="sxs-lookup"><span data-stu-id="eb82c-109">Gets a pointer to the next `IInstallReferenceItem` contained in this `IInstallReferenceEnum`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="eb82c-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="eb82c-110">Requirements</span></span>  
 <span data-ttu-id="eb82c-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb82c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb82c-112">**En-tête :** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="eb82c-112">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="eb82c-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb82c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb82c-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eb82c-114">See also</span></span>

- [<span data-ttu-id="eb82c-115">Interfaces de fusion</span><span class="sxs-lookup"><span data-stu-id="eb82c-115">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [<span data-ttu-id="eb82c-116">IInstallReferenceItem, interface</span><span class="sxs-lookup"><span data-stu-id="eb82c-116">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)
