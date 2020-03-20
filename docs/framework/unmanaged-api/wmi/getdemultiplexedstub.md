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
# <a name="getdemultiplexedstub-function"></a>GetDemultiplexedStub, fonction
Crée un récepteur de redirecteur d’objet pour aider un client lors de la réception des appels asynchrones WMI.
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetDemultiplexedStub (
   [in] IUnknown*    pObject,
   [in] boolean      isLocal,
   [out] IUnknown**  ppObject
);
```  

## <a name="parameters"></a>Paramètres

`pObject`  
[dans] Un pointeur à la mise en œuvre en cours du client [d’IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink).

`isLocal`  
[dans] Un drapeau qui indique si`true`l’événement est local (); autrement, `false`.

`ppObject`  
[out] Un expéditeur d’objets coule pour aider un client à recevoir des appels asynchrones de Windows Management.

## <a name="return-value"></a>Valeur retournée

Si la fonction réussit, `S_OK` la valeur de rendement est (0).

Si la fonction échoue, la valeur de retour est un code d’erreur non nul. Pour obtenir des informations d’erreur étendues, appelez la fonction [GetErrorInfo.](geterrorinfo.md)

## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête:** WMINet_Utils.idl  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
