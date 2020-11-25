---
title: Fonction GetMethodOrigin (référence des API non managées)
description: La fonction GetMethodOrigin détermine la classe dans laquelle une méthode est déclarée.
ms.date: 11/06/2017
api_name:
- GetMethodOrigin
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethodOrigin
helpviewer_keywords:
- GetMethodOrigin function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 434392ffb4d9124e319bcd9c42fdd340d3fec5b4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722776"
---
# <a name="getmethodorigin-function"></a>GetMethodOrigin, fonction

Détermine la classe dans laquelle une méthode est déclarée.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMethodOrigin (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
);
```  

## <a name="parameters"></a>Paramètres

`vFunc`  
dans Ce paramètre n’est pas utilisé.

`ptr`  
dans Pointeur vers une instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

`wszMethodName`  
dans Nom de la méthode pour l’objet dont la classe propriétaire est demandée.

`pstrClassName`  
à Reçoit le nom de la classe qui possède la méthode.

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :

|Constante  |Value  |Description  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | 0x80041002 | La méthode spécifiée est introuvable. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Un ou plusieurs paramètres ne sont pas valides. |
|`WBEM_S_NO_ERROR` | 0 | L’appel de la fonction a réussi.  |
  
## <a name="remarks"></a>Remarques

Cette fonction encapsule un appel à la méthode [IWbemClassObject :: GetMethodOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) .

Étant donné qu’une classe peut hériter de méthodes d’une ou plusieurs classes de base, les développeurs veulent souvent déterminer la classe dans laquelle une méthode donnée est définie.

Le `pstrClassName` paramètre ne doit pas pointer vers un valide `BSTR` avant que la fonction soit appelée, car il s’agit d’un `out` paramètre ; ce pointeur n’est pas libéré après le retour de la fonction.

## <a name="requirements"></a>Configuration requise  

**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils. idl  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
