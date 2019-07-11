---
title: GetNames (fonction) (référence des API non managées)
description: La fonction GetNames récupère les noms des propriétés d’un objet.
ms.date: 11/06/2017
api_name:
- GetNames
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetNames
helpviewer_keywords:
- GetNames function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e75bf9aab820216373f2f33fe8aa567f10befcb1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746520"
---
# <a name="getnames-function"></a>GetNames, fonction
Récupère une partie ou l’ensemble des noms des propriétés d’un objet. 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetNames (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszQualifierName,
   [in] LONG                lFlags,
   [in] VARIANT*            pQualifierValue,
   [out] SAFEARRAY (BSTR)** pstrNames
); 
```  

## <a name="parameters"></a>Paramètres

`vFunc`  
[in] Ce paramètre n’est pas utilisé.

`ptr`  
[in] Un pointeur vers un [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.

`wszQualifierName`  
[in] Un pointeur vers une valide `LPCWSTR` qui spécifie un nom de qualificateur qui opère en tant que partie d’un filtre. Pour plus d’informations, consultez le [notes](#remarks) section. Ce paramètre peut être `null`. 

`lFlags`  
[in] Une combinaison des champs de bits. Pour plus d’informations, consultez le [notes](#remarks) section.

`pQualifierValue`   
[in] Un pointeur vers une valide `VARIANT` structure initialisé à une valeur de filtre. Ce paramètre peut être `null`. 

`pstrNames`  
[out] Un `SAFEARRAY` structure qui contient les noms de propriété. À l’entrée, ce paramètre doit toujours être un pointeur vers `null`. Consultez le [notes](#remarks) section pour plus d’informations. 

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :

|Constante  |Valeur  |Description  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Il y a eu une défaillance générale. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Un ou plusieurs paramètres ne sont pas valides, ou une combinaison incorrecte des indicateurs et des paramètres a été spécifiée. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Mémoire est insuffisante pour terminer l’opération. |
|`WBEM_S_NO_ERROR` | 0 | L’appel de fonction a réussi.  |
  
## <a name="remarks"></a>Notes

Cette fonction encapsule un appel à la [IWbemClassObject::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) (méthode).

Nommé retourné est contrôlé par une combinaison d’indicateurs et de paramètres. Par exemple, la fonction peut retourner les noms de toutes les propriétés ou uniquement les noms des propriétés de clé.  Le filtre principal est spécifié dans le `lFlags` paramètre et les autres paramètres dépendent.

L’indicateur des valeurs dans `lFlags` sont des champs de bits

Les indicateurs qui peuvent être passés en tant que le `lEnumFlags` argument sont des champs de bits qui sont définis dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code.  Vous pouvez combiner un indicateur de chaque groupe avec n’importe quel indicateur à partir d’un autre groupe. Toutefois, les indicateurs à partir du même groupe sont mutuellement exclusifs. 

| Indicateurs de groupe 1 |Valeur  |Description  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | 0 | Retourner tous les noms de propriété. `strQualifierName` et `pQualifierVal` ne sont pas utilisés. |
| `WBEM_FLAG_ONLY_IF_TRUE` | 1 | Retourner uniquement des propriétés qui ont un qualificateur de nom spécifié par le `strQualifierName` paramètre. Si cet indicateur est utilisé, vous devez spécifier `strQualifierName`. |
|`WBEM_FLAG_ONLY_IF_FALSE` | 2 |  Retourner uniquement des propriétés qui n’ont pas d’un qualificateur de nom spécifié par le `strQualifierName` paramètre. Si cet indicateur est utilisé, vous devez spécifier `strQualifierName`. |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | 3 | Retourne uniquement les propriétés qui ont un qualificateur de nom spécifié par le `wszQualifierName` paramètre et également avoir une valeur identique à celui spécifié par le `pQualifierVal` structure. Si cet indicateur est utilisé, vous devez spécifier à la fois un `wszQualifierName` et un `pQualifierValue`. |

| Indicateurs de groupe 2 |Valeur  |Description  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | 0x4 | Retourner uniquement les noms des propriétés qui définissent les clés. |
|`WBEM_FLAG_REFS_ONLY` | 0x8 | Retour seuls noms de propriétés qui sont des références d’objet. |

| Indicateurs de groupe 3 |`Value`  |Description  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Retourner uniquement les noms de propriétés qui appartiennent à la classe la plus dérivée. Exclure les propriétés des classes parentes. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Retourner uniquement les noms de propriétés qui appartiennent à des classes parentes. |
|`WBEM_FLAG_SYSTEM_ONLY` | 0x30 | Retourner uniquement les noms des propriétés système. |
|`WBEM_FLAG_NONSYSTEM_ONLY` | 0x40 | Retourner uniquement les noms des propriétés non système. |

La fonction alloue toujours un nouveau `SAFEARRAY` si elle retourne `WBEM_S_NO_ERROR`, et `pstrNames` est toujours défini pour pointer vers elle. Le tableau retourné peut avoir les éléments 0 si aucune propriété correspondent aux filtres spécifiés. Si la fonction retourne une valeur autre que `WBM_S_NO_ERROR`, un nouveau `SAFEARRAY` structure n’est pas retournée.
 
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils.idl  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
