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
ms.openlocfilehash: 0d29b9e2a9b9022f682065816a62734d6c5b2d62
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796409"
---
# <a name="iinstallreferenceenum-interface"></a><span data-ttu-id="40fee-102">IInstallReferenceEnum, interface</span><span class="sxs-lookup"><span data-stu-id="40fee-102">IInstallReferenceEnum Interface</span></span>
<span data-ttu-id="40fee-103">Représente un énumérateur pour les assemblys référencés installés dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="40fee-103">Represents an enumerator for the referenced assemblies installed in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40fee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40fee-104">Syntax</span></span>  
  
```cpp  
interface IInstallReferenceEnum : IUnknown {  
    HRESULT GetNextInstallReferenceItem (  
        [out] IInstallReferenceItem **ppRefItem,  
        [in]  DWORD dwFlags,  
        [in]  LPVOID pvReserved  
    );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="40fee-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="40fee-105">Methods</span></span>  
  
|<span data-ttu-id="40fee-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="40fee-106">Method</span></span>|<span data-ttu-id="40fee-107">Description</span><span class="sxs-lookup"><span data-stu-id="40fee-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="40fee-108">GetNextInstallReferenceItem, méthode</span><span class="sxs-lookup"><span data-stu-id="40fee-108">GetNextInstallReferenceItem Method</span></span>](iinstallreferenceenum-getnextinstallreferenceitem-method.md)|<span data-ttu-id="40fee-109">Obtient un pointeur vers le suivant `IInstallReferenceItem` contenu dans ce `IInstallReferenceEnum`.</span><span class="sxs-lookup"><span data-stu-id="40fee-109">Gets a pointer to the next `IInstallReferenceItem` contained in this `IInstallReferenceEnum`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="40fee-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="40fee-110">Requirements</span></span>  
 <span data-ttu-id="40fee-111">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40fee-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40fee-112">**En-tête :** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="40fee-112">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="40fee-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40fee-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40fee-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="40fee-114">See also</span></span>

- [<span data-ttu-id="40fee-115">Interfaces de fusion</span><span class="sxs-lookup"><span data-stu-id="40fee-115">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="40fee-116">IInstallReferenceItem, interface</span><span class="sxs-lookup"><span data-stu-id="40fee-116">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)
