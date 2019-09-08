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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a2d3885a4a9e54950909053ba18de5b1891e7edf
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798611"
---
# <a name="getdemultiplexedstub-function"></a>GetDemultiplexedStub fonction)
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
dans Pointeur vers l’implémentation in-process du client de [IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink).

`isLocal`  
dans Indicateur qui signale si l’événement est local (`true`); sinon, `false`.

`ppObject`  
à Récepteur de redirecteur d’objet pour aider un client à recevoir des appels asynchrones de la gestion Windows.

## <a name="return-value"></a>Valeur de retour

Si la fonction est réussie, la valeur de retour `S_OK` est (0).

Si la fonction échoue, la valeur de retour est un code d’erreur différent de zéro. Pour afficher les informations d’erreur étendues, appelez la fonction [GetErrorInfo](geterrorinfo.md) .
    
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils.idl  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performance (informations de référence sur les API non managées)](index.md)
