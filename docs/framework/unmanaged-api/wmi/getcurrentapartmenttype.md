---
title: Fonction GetCurrentApartmentType (Référence API non gestion)
description: La fonction GetCurrentApartmentType récupère le type d’appartement dans lequel l’appelant exécute.
ms.date: 11/06/2017
api_name:
- GetCurrentApartmentType
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetCurrentApartmentType
helpviewer_keywords:
- GetCurrentApartmentType function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 3fc88f7997ee5a6c25359243e1ee97a041050eb7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176823"
---
# <a name="getcurrentapartmenttype-function"></a>GetCurrentApartmentType, fonction
Récupère le type de cloisonnement dans lequel l’appelant s’exécute.
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCurrentApartmentType (
   [in] int                   vFunc,
   [in] IComThreadingInfo*    ptr,
   [out] APTTYPE*             aptType
);
```  

## <a name="parameters"></a>Paramètres

`vFunc`  
[dans] Ce paramètre n’est pas utilisé.

`ptr`  
[dans] Un pointeur à une instance [IComThreadingInfo.](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo)

`aptType`  
[out] Un pointeur à une valeur de recensement [APTTYPE](/windows/win32/api/objidlbase/ne-objidlbase-apttype) qui indique l’appartement de l’appelant.

## <a name="return-value"></a>Valeur retournée

|Constant  |Valeur  |Description  |
|---------|---------|---------|
| `S_OK` | 0 | La fonction s’est terminée avec succès. |
| `E_FAIL` | 0x80000008 | L’appelant ne s’exécute pas dans un appartement. |
  
## <a name="remarks"></a>Notes 

Cette fonction enveloppe un appel à [l’IComThreadingInfo::GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) méthode.

## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête:** WMINet_Utils.idl  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
