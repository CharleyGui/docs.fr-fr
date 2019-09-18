---
title: IEnumRAWINPUTDEVIC:Clone
ms.date: 03/30/2017
helpviewer_keywords:
- Clone method [WPF]
ms.assetid: 2a6a1900-aa55-45fa-9382-241d569a2dc4
ms.openlocfilehash: cd634b4d4a88d83d425b787ed8493f9aa2504988
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053418"
---
# <a name="ienumrawinputdevicclone"></a><span data-ttu-id="10bea-102">IEnumRAWINPUTDEVIC:Clone</span><span class="sxs-lookup"><span data-stu-id="10bea-102">IEnumRAWINPUTDEVIC:Clone</span></span>
<span data-ttu-id="10bea-103">Crée un autre énumérateur de périphériques d'entrée brute avec le même état que l'énumérateur actif pour itérer au sein de la même liste.</span><span class="sxs-lookup"><span data-stu-id="10bea-103">Creates another raw input device enumerator with the same state as the current enumerator to iterate over the same list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10bea-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="10bea-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone( [out] IEnumRAWINPUTDEVICE **ppenum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="10bea-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="10bea-105">Parameters</span></span>  
 `ppenum`  
  
 <span data-ttu-id="10bea-106">à Adresse de la variable de sortie qui reçoit le pointeur d’interface [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md) .</span><span class="sxs-lookup"><span data-stu-id="10bea-106">[out] Address of output variable that receives the [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md) interface pointer.</span></span> <span data-ttu-id="10bea-107">Si la méthode échoue, la valeur de cette variable de sortie n’est pas définie.</span><span class="sxs-lookup"><span data-stu-id="10bea-107">If the method is unsuccessful, the value of this output variable is undefined.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="10bea-108">Valeur de propriété/valeur de retour</span><span class="sxs-lookup"><span data-stu-id="10bea-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="10bea-109">HRESULT : Cette méthode prend en charge les valeurs de retour E_INVALIDARG, E_OUTOFMEMORY et E_UNEXPECTED standard.</span><span class="sxs-lookup"><span data-stu-id="10bea-109">HRESULT: This method supports the standard return values E_INVALIDARG, E_OUTOFMEMORY, and E_UNEXPECTED.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="10bea-110">Notes</span><span class="sxs-lookup"><span data-stu-id="10bea-110">Remarks</span></span>  
 <span data-ttu-id="10bea-111">Cette méthode permet d’enregistrer un point dans la séquence d’énumération afin de retourner ultérieurement à ce point.</span><span class="sxs-lookup"><span data-stu-id="10bea-111">This method makes it possible to record a point in the enumeration sequence in order to return to that point at a later time.</span></span> <span data-ttu-id="10bea-112">L’appelant doit libérer ce nouvel énumérateur séparément du premier énumérateur.</span><span class="sxs-lookup"><span data-stu-id="10bea-112">The caller must release this new enumerator separately from the first enumerator.</span></span>
