---
title: Fonction clone (référence API non gestion)
description: La fonction Clone renvoie un nouvel objet qui est un clone complet de l’actuel.
ms.date: 11/06/2017
api_name:
- Clone
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Clone
helpviewer_keywords:
- Clone function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: cb4951a1f289417482bfa1287028cc66349a5938
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176849"
---
# <a name="clone-function"></a>Clone, fonction
Retourne un nouvel objet qui est un clone complet de l’objet actuel.
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Clone (
   [in] int                  vFunc,
   [in] IWbemClassObject*    ptr,
   [out] IWbemClassObject**  ppCopy
);
```  

## <a name="parameters"></a>Paramètres

`vFunc`  
[dans] Ce paramètre n’est pas utilisé.

`ptr`  
[dans] Un pointeur à une instance [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)

`ppCopy`  
[out] Un nouvel objet qui est `ptr`un solitaire complet de . Cet argument `null` ne peut pas être si elle reçoit la copie de l’objet actuel.

## <a name="return-value"></a>Valeur retournée

Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli.h,* ou vous pouvez les définir comme des constantes dans votre code :

|Constant  |Valeur  |Description  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Il y a eu un échec général. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `null`a été spécifié comme un paramètre, et il n’est pas légal dans cette utilisation. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Pas assez de mémoire est disponible pour cloner l’objet. |
| `WBEM_S_NO_ERROR` | 0 | L’appel de fonction a été réussi.  |
  
## <a name="remarks"></a>Notes 

Cette fonction enveloppe un appel à [l’IWbemClassObject::Méthode Clone.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone)

L’objet cloné est un objet COM qui a un nombre de références de 1.

## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête:** WMINet_Utils.idl  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
