---
title: Fonction GetErrorInfo (référence des API non managées)
description: La fonction GetErrorInfo récupère les informations d’erreur de l’appel de fonction précédent.
ms.date: 11/06/2017
api_name:
- GetErrorInfo
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetErrorInfo
helpviewer_keywords:
- GetErrorInfo function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 9a80c0b5522113e704336cda29362a0406077931
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90553673"
---
# <a name="geterrorinfo-function"></a>GetErrorInfo, fonction
Récupère les informations d’erreur à partir de l’appel de fonction précédent.  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
IErrorInfo* GetErrorInfo();
```  

## <a name="return-value"></a>Valeur renvoyée

Pointeur vers un objet [IErrorInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) si l’appel de fonction réussit, ou en `null` cas d’échec.
  
## <a name="remarks"></a>Notes

Cette fonction encapsule un appel à la méthode [IComThreadingInfo :: GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) .

## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils. def  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
