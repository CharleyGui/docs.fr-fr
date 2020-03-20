---
title: Fonction GetDemultiplexedStub (référence API non gémanisée)
description: La fonction GetDemultiplexedStub crée un évier d’expéditeur d’objets pour aider un client à recevoir des appels asynchrones de Windows Management.
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
ms.openlocfilehash: d15fed261db2ca2cda6dbf824dc9cb0d5c56eed3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174964"
---
# <a name="getdemultiplexedstub-function"></a><span data-ttu-id="648ce-103">GetDemultiplexedStub, fonction</span><span class="sxs-lookup"><span data-stu-id="648ce-103">GetDemultiplexedStub function</span></span>
<span data-ttu-id="648ce-104">Crée un récepteur de redirecteur d’objet pour aider un client lors de la réception des appels asynchrones WMI.</span><span class="sxs-lookup"><span data-stu-id="648ce-104">Creates an object forwarder sink to assist a client in receiving asynchronous calls from Windows Management.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="648ce-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="648ce-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDemultiplexedStub (
   [in] IUnknown*    pObject,
   [in] boolean      isLocal,
   [out] IUnknown**  ppObject
);
```  

## <a name="parameters"></a><span data-ttu-id="648ce-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="648ce-106">Parameters</span></span>

`pObject`  
<span data-ttu-id="648ce-107">[dans] Un pointeur à la mise en œuvre en cours du client [d’IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink).</span><span class="sxs-lookup"><span data-stu-id="648ce-107">[in] A pointer to the client's in-process implementation of [IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink).</span></span>

`isLocal`  
<span data-ttu-id="648ce-108">[dans] Un drapeau qui indique si`true`l’événement est local (); autrement, `false`.</span><span class="sxs-lookup"><span data-stu-id="648ce-108">[in] A flag that indicates whether the event is local (`true`); otherwise, `false`.</span></span>

`ppObject`  
<span data-ttu-id="648ce-109">[out] Un expéditeur d’objets coule pour aider un client à recevoir des appels asynchrones de Windows Management.</span><span class="sxs-lookup"><span data-stu-id="648ce-109">[out] A object forwarder sink to assist a client in receiving asynchronous calls from Windows Management.</span></span>

## <a name="return-value"></a><span data-ttu-id="648ce-110">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="648ce-110">Return value</span></span>

<span data-ttu-id="648ce-111">Si la fonction réussit, `S_OK` la valeur de rendement est (0).</span><span class="sxs-lookup"><span data-stu-id="648ce-111">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="648ce-112">Si la fonction échoue, la valeur de retour est un code d’erreur non nul.</span><span class="sxs-lookup"><span data-stu-id="648ce-112">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="648ce-113">Pour obtenir des informations d’erreur étendues, appelez la fonction [GetErrorInfo.](geterrorinfo.md)</span><span class="sxs-lookup"><span data-stu-id="648ce-113">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="648ce-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="648ce-114">Requirements</span></span>  
 <span data-ttu-id="648ce-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="648ce-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="648ce-116">**En-tête:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="648ce-116">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="648ce-117">**.NET Versions-cadre:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="648ce-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="648ce-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="648ce-118">See also</span></span>

- [<span data-ttu-id="648ce-119">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="648ce-119">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
