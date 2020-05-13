---
title: ICorDebugSymbolProvider2, interface
ms.date: 03/30/2017
ms.assetid: 1c9c3d92-f0de-4d4d-87f1-0c702a4808af
ms.openlocfilehash: e6712dca776bf4c20ce7fc8568e94399a81beecb
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379298"
---
# <a name="icordebugsymbolprovider2-interface"></a><span data-ttu-id="fbd1d-102">ICorDebugSymbolProvider2, interface</span><span class="sxs-lookup"><span data-stu-id="fbd1d-102">ICorDebugSymbolProvider2 Interface</span></span>
<span data-ttu-id="fbd1d-103">Étend logiquement l’interface [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) pour récupérer des informations supplémentaires sur les symboles de débogage.</span><span class="sxs-lookup"><span data-stu-id="fbd1d-103">Logically extends the [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fbd1d-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="fbd1d-104">Methods</span></span>  
  
|<span data-ttu-id="fbd1d-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="fbd1d-105">Method</span></span>|<span data-ttu-id="fbd1d-106">Description</span><span class="sxs-lookup"><span data-stu-id="fbd1d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fbd1d-107">GetFrameProps, méthode</span><span class="sxs-lookup"><span data-stu-id="fbd1d-107">GetFrameProps Method</span></span>](icordebugsymbolprovider2-getframeprops-method.md)|<span data-ttu-id="fbd1d-108">Retourne l'adresse virtuelle relative de départ d'une méthode et le frame parent en fonction d'une adresse virtuelle relative de code.</span><span class="sxs-lookup"><span data-stu-id="fbd1d-108">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>|  
|[<span data-ttu-id="fbd1d-109">GetGenericDictionaryInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="fbd1d-109">GetGenericDictionaryInfo Method</span></span>](icordebugsymbolprovider2-getgenericdictionaryinfo-method.md)|<span data-ttu-id="fbd1d-110">Récupère un mappage de dictionnaire générique.</span><span class="sxs-lookup"><span data-stu-id="fbd1d-110">Retrieves a generic dictionary map.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fbd1d-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="fbd1d-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fbd1d-112">Cette interface est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="fbd1d-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="fbd1d-113">Si vous implémentez cette interface pour des scénarios ICorDebug en dehors de .NET Native, le Common Language Runtime ignore cette interface.</span><span class="sxs-lookup"><span data-stu-id="fbd1d-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbd1d-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="fbd1d-114">Requirements</span></span>  
 <span data-ttu-id="fbd1d-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fbd1d-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbd1d-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fbd1d-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fbd1d-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fbd1d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fbd1d-118">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbd1d-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbd1d-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fbd1d-119">See also</span></span>

- [<span data-ttu-id="fbd1d-120">ICorDebugSymbolProvider, interface</span><span class="sxs-lookup"><span data-stu-id="fbd1d-120">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="fbd1d-121">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="fbd1d-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="fbd1d-122">Débogage</span><span class="sxs-lookup"><span data-stu-id="fbd1d-122">Debugging</span></span>](index.md)
