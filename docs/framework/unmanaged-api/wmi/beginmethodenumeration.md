---
title: Fonction BeginMethodEnumeration (référence des API non managées)
description: La fonction BeginMethodEnumeration commence une énumération des méthodes de l’objet
ms.date: 11/06/2017
api_name:
- BeginMethodEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BeginMethodEnumeration
helpviewer_keywords:
- BeginMethodEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: a72d61a572a0582ed8c03e56a8a9933c5f2775f0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719760"
---
# <a name="beginmethodenumeration-function"></a>BeginMethodEnumeration, fonction

Commence une énumération des méthodes disponibles pour l’objet.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT BeginMethodEnumeration (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              lEnumFlags
);
```  

## <a name="parameters"></a>Paramètres

`vFunc`  
dans Ce paramètre n’est pas utilisé.

`ptr`  
dans Pointeur vers une instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

`lEnumFlags`  
dans Zéro (0) pour toutes les méthodes, ou un indicateur qui spécifie la portée de l’énumération. Les indicateurs suivants sont définis dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :

Constante  |Value  |Description  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Limitez l’énumération aux méthodes définies dans la classe elle-même. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Limitez l’énumération aux propriétés héritées des classes de base. |

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :

|Constante  |Value  |Description  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | `lEnnumFlags` est différent de zéro et n’est pas l’un des indicateurs spécifiés. |
|`WBEM_S_NO_ERROR` | 0 | L’appel de la fonction a réussi.  |
  
## <a name="remarks"></a>Remarques

Cette fonction encapsule un appel à la méthode [IWbemClassObject :: BeginMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-beginmethodenumeration) .

Cet appel de méthode est pris en charge uniquement si l’objet actuel est une définition de classe. La manipulation de méthode n’est pas disponible à partir de pointeurs [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) qui pointent vers des instances. L’ordre dans lequel les méthodes sont énumérées est toujours indifférent pour une instance donnée de [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject).

## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils. idl  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
