---
title: Fonction GetDemultiplexedStub (référence des API non managées)
description: La fonction GetDemultiplexedStub crée un récepteur de redirecteur d’objet pour aider un client à recevoir des appels asynchrones de la gestion Windows.
ms.date: 11/06/2017
api_name:
- GetDemultiplexedStub
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetDemultiplexedStub
helpviewer_keywords:
- GetDemultiplexedStub function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: f8f9b56268168bb16c476a9366facd17e8ac44e5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730628"
---
# <a name="getdemultiplexedstub-function"></a><span data-ttu-id="61c99-103">GetDemultiplexedStub, fonction</span><span class="sxs-lookup"><span data-stu-id="61c99-103">GetDemultiplexedStub function</span></span>

<span data-ttu-id="61c99-104">Crée un récepteur de redirecteur d’objet pour aider un client lors de la réception des appels asynchrones WMI.</span><span class="sxs-lookup"><span data-stu-id="61c99-104">Creates an object forwarder sink to assist a client in receiving asynchronous calls from Windows Management.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="61c99-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="61c99-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDemultiplexedStub (
   [in] IUnknown*    pObject,
   [in] boolean      isLocal,
   [out] IUnknown**  ppObject
);
```  

## <a name="parameters"></a><span data-ttu-id="61c99-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="61c99-106">Parameters</span></span>

`pObject`  
<span data-ttu-id="61c99-107">dans Pointeur vers l’implémentation in-process du client de [IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink).</span><span class="sxs-lookup"><span data-stu-id="61c99-107">[in] A pointer to the client's in-process implementation of [IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink).</span></span>

`isLocal`  
<span data-ttu-id="61c99-108">dans Indicateur qui signale si l’événement est local ( `true` ); sinon, `false` .</span><span class="sxs-lookup"><span data-stu-id="61c99-108">[in] A flag that indicates whether the event is local (`true`); otherwise, `false`.</span></span>

`ppObject`  
<span data-ttu-id="61c99-109">à Récepteur de redirecteur d’objet pour aider un client à recevoir des appels asynchrones de la gestion Windows.</span><span class="sxs-lookup"><span data-stu-id="61c99-109">[out] A object forwarder sink to assist a client in receiving asynchronous calls from Windows Management.</span></span>

## <a name="return-value"></a><span data-ttu-id="61c99-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="61c99-110">Return value</span></span>

<span data-ttu-id="61c99-111">Si la fonction est réussie, la valeur de retour est `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="61c99-111">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="61c99-112">Si la fonction échoue, la valeur de retour est un code d’erreur différent de zéro.</span><span class="sxs-lookup"><span data-stu-id="61c99-112">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="61c99-113">Pour afficher les informations d’erreur étendues, appelez la fonction [GetErrorInfo](geterrorinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="61c99-113">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="61c99-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="61c99-114">Requirements</span></span>  

 <span data-ttu-id="61c99-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61c99-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61c99-116">**En-tête :** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="61c99-116">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="61c99-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="61c99-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61c99-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="61c99-118">See also</span></span>

- [<span data-ttu-id="61c99-119">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="61c99-119">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
