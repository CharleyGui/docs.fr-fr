---
title: Fonction WritePropertyValue (Référence API non gestion)
description: La fonction WritePropertyValue écrit des octets à une propriété.
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
ms.openlocfilehash: 4a950beef2e9bf8c0230d6a38008d75f89373410
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174834"
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
[dans] Ce paramètre n’est pas utilisé.

`ptr`  
[dans] Un pointeur à une instance [IWbemObjectAccess.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess)

`lHandle`  
[dans] Un intégrier qui contient la poignée qui identifie cette propriété. Le manche peut être récupéré en appelant la fonction [GetPropertyHandle.](getpropertyhandle.md)

`lNumBytes`  
[dans] Le nombre d’octets écrits à la propriété. Consultez la section [Remarques](#remarks) pour plus d’informations.

`pHandle`[out] Un pointeur vers le tableau d’en-avant qui contient les données.

## <a name="return-value"></a>Valeur retournée

Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli.h,* ou vous pouvez les définir comme des constantes dans votre code :

|Constant  |Valeur  |Description  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Un paramètre n'est pas valide. |
|`WBEM_E_TYPE_MISMATCH` | 0x80041005 | Une incompatibilité de type est survenue. |
|`WBEM_S_NO_ERROR` | 0 | L’appel de fonction a été réussi.  |
  
## <a name="remarks"></a>Notes 

Cette fonction enveloppe un appel à [l’IWbemClassObject::WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) méthode.

Utilisez cette fonction pour définir la`DWORD` chaîne`QWORD` et toutes les autres données non ou non.

Pour les valeurs des `lNumBytes` propriétés noncordes, doit être la bonne taille de données du type de propriété spécifiée. Pour les valeurs `lNumBytes` de propriété de chaîne, doit être la longueur de la chaîne spécifiée dans les octets, et la chaîne elle-même doit être d’une longueur égale dans les octets et être suivie avec un caractère de terminaison nulle.

## <a name="requirements"></a>Spécifications  
**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête:** WMINet_Utils.idl  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
