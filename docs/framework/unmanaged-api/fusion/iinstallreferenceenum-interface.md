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
ms.openlocfilehash: f56a9049cd4b503124abe9dd4866dc91779e268e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721060"
---
# <a name="iinstallreferenceenum-interface"></a><span data-ttu-id="105ec-102">IInstallReferenceEnum, interface</span><span class="sxs-lookup"><span data-stu-id="105ec-102">IInstallReferenceEnum Interface</span></span>

<span data-ttu-id="105ec-103">Représente un énumérateur pour les assemblys référencés installés dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="105ec-103">Represents an enumerator for the referenced assemblies installed in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="105ec-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="105ec-104">Syntax</span></span>  
  
```cpp  
interface IInstallReferenceEnum : IUnknown {  
    HRESULT GetNextInstallReferenceItem (  
        [out] IInstallReferenceItem **ppRefItem,  
        [in]  DWORD dwFlags,  
        [in]  LPVOID pvReserved  
    );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="105ec-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="105ec-105">Methods</span></span>  
  
|<span data-ttu-id="105ec-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="105ec-106">Method</span></span>|<span data-ttu-id="105ec-107">Description</span><span class="sxs-lookup"><span data-stu-id="105ec-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="105ec-108">GetNextInstallReferenceItem, méthode</span><span class="sxs-lookup"><span data-stu-id="105ec-108">GetNextInstallReferenceItem Method</span></span>](iinstallreferenceenum-getnextinstallreferenceitem-method.md)|<span data-ttu-id="105ec-109">Obtient un pointeur vers le suivant `IInstallReferenceItem` contenu dans ce `IInstallReferenceEnum` .</span><span class="sxs-lookup"><span data-stu-id="105ec-109">Gets a pointer to the next `IInstallReferenceItem` contained in this `IInstallReferenceEnum`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="105ec-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="105ec-110">Requirements</span></span>  

 <span data-ttu-id="105ec-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="105ec-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="105ec-112">**En-tête :** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="105ec-112">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="105ec-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="105ec-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="105ec-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="105ec-114">See also</span></span>

- [<span data-ttu-id="105ec-115">Interfaces de fusion</span><span class="sxs-lookup"><span data-stu-id="105ec-115">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="105ec-116">IInstallReferenceItem, interface</span><span class="sxs-lookup"><span data-stu-id="105ec-116">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)
