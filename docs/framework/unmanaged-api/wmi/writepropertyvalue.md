---
title: Fonction WritePropertyValue (référence des API non managées)
description: La fonction WritePropertyValue écrit des octets dans une propriété.
ms.date: 11/06/2017
api_name:
- WritePropertyValue
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- WritePropertyValue
helpviewer_keywords:
- WritePropertyValue function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: e225516b06c477dc1a24cf721bc3e1ade9076b75
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729406"
---
# <a name="writepropertyvalue-function"></a>WritePropertyValue, fonction

Écrit un nombre spécifié d’octets dans une propriété identifiée par un descripteur de propriété.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT WritePropertyValue (
   [in] int                  vFunc,
   [in] IWbemObjectAccess*   ptr,
   [in] long                 lHandle,
   [in] long                 lNumBytes,
   [in] byte*                aData
);
```  

## <a name="parameters"></a>Paramètres

`vFunc`  
dans Ce paramètre n’est pas utilisé.

`ptr`  
dans Pointeur vers une instance [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) .

`lHandle`  
dans Entier qui contient le handle qui identifie cette propriété. Le descripteur peut être récupéré en appelant la fonction [GetPropertyHandle](getpropertyhandle.md) .

`lNumBytes`  
dans Nombre d’octets écrits dans la propriété. Pour plus d’informations, consultez la section [Notes](#remarks) .

`pHandle` à Pointeur vers le tableau d’octets qui contient les données.

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :

|Constante  |Value  |Description  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Un paramètre n'est pas valide. |
|`WBEM_E_TYPE_MISMATCH` | 0x80041005 | Une incompatibilité de type est survenue. |
|`WBEM_S_NO_ERROR` | 0 | L’appel de la fonction a réussi.  |
  
## <a name="remarks"></a>Remarques

Cette fonction encapsule un appel à la méthode [IWbemClassObject :: WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) .

Utilisez cette fonction pour définir la chaîne et toutes les autres `DWORD` données non ou non `QWORD` .

Pour les valeurs de propriété qui `lNumBytes` ne sont pas de type chaîne, doit être la bonne taille de données du type de propriété spécifié. Pour les valeurs de propriété de type chaîne, `lNumBytes` doit correspondre à la longueur de la chaîne spécifiée en octets, et la chaîne elle-même doit être de longueur égale en octets et être suivie d’un caractère de fin null.

## <a name="requirements"></a>Configuration requise  

**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils. idl  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
