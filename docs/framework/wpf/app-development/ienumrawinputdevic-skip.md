---
title: IEnumRAWINPUTDEVIC:Skip
ms.date: 03/30/2017
helpviewer_keywords:
- Skip method [WPF]
ms.assetid: c967b0f8-1c6a-459c-8c16-d4f08918ab65
ms.openlocfilehash: a74f71345a22f6d766c2d5966ca5d2cb33ab756e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053375"
---
# <a name="ienumrawinputdevicskip"></a><span data-ttu-id="c2e0b-102">IEnumRAWINPUTDEVIC:Skip</span><span class="sxs-lookup"><span data-stu-id="c2e0b-102">IEnumRAWINPUTDEVIC:Skip</span></span>
<span data-ttu-id="c2e0b-103">Indique à l’énumérateur d’ignorer les éléments `celt` suivants dans l’énumération afin que l’appel suivant à [IEnumRAWINPUTDEVIC : Next](ienumrawinputdevic-next.md) ne retourne pas ces éléments.</span><span class="sxs-lookup"><span data-stu-id="c2e0b-103">Instructs the enumerator to skip the next `celt` elements in the enumeration so that the next call to [IEnumRAWINPUTDEVIC:Next](ienumrawinputdevic-next.md) will not return those elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2e0b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c2e0b-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip( [in] ULONG celt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2e0b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c2e0b-105">Parameters</span></span>  
 `celt`  
  
 <span data-ttu-id="c2e0b-106">dans Nombre d’éléments à ignorer.</span><span class="sxs-lookup"><span data-stu-id="c2e0b-106">[in] Number of elements to be skipped.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="c2e0b-107">Valeur de propriété/valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c2e0b-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="c2e0b-108">HRESULT : S_OK si le nombre d’éléments fourni est `celt`; S_FALSE dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="c2e0b-108">HRESULT: S_OK if the number of elements supplied is `celt`; S_FALSE otherwise.</span></span>
