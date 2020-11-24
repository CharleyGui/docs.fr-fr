---
title: Fonction GetNames (référence des API non managées)
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
ms.openlocfilehash: fd889158e61b86f42d88bcf86eda7d816277e6ac
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687656"
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
dans Ce paramètre n’est pas utilisé.

`ptr`  
dans Pointeur vers une instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

`wszQualifierName`  
dans Pointeur vers un valide `LPCWSTR` qui spécifie un nom de qualificateur qui opère dans le cadre d’un filtre. Pour plus d’informations, consultez la section [Notes](#remarks) . Ce paramètre peut être `null`.

`lFlags`  
dans Combinaison de champs de bits. Pour plus d’informations, consultez la section [Notes](#remarks) .

`pQualifierValue` dans Pointeur vers une structure valide `VARIANT` initialisée à une valeur de filtre. Ce paramètre peut être `null`.

`pstrNames`  
à `SAFEARRAY` Structure qui contient des noms de propriété. Dans l’entrée, ce paramètre doit toujours être un pointeur vers `null` . Pour plus d’informations, consultez la section [Notes](#remarks) .

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :

|Constante  |Value  |Description  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Une défaillance générale s’est produite. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Un ou plusieurs paramètres ne sont pas valides ou une combinaison incorrecte d’indicateurs et de paramètres a été spécifiée. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | La mémoire n'est pas suffisante pour terminer cette opération. |
|`WBEM_S_NO_ERROR` | 0 | L’appel de la fonction a réussi.  |
  
## <a name="remarks"></a>Remarques

Cette fonction encapsule un appel à la méthode [IWbemClassObject :: GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) .

Le nommé retourné est contrôlé par une combinaison d’indicateurs et de paramètres. Par exemple, la fonction peut retourner les noms de toutes les propriétés ou uniquement les noms des propriétés de clé.  Le filtre principal est spécifié dans le `lFlags` paramètre, et les autres paramètres varient en fonction de celui-ci.

Les valeurs d’indicateur dans `lFlags` sont des champs de bits

Les indicateurs qui peuvent être passés en tant qu' `lEnumFlags` argument sont des champs de bits définis dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code.  Vous pouvez associer un indicateur de chaque groupe à n’importe quel indicateur de n’importe quel autre groupe. Toutefois, les indicateurs du même groupe s’excluent mutuellement.

| Indicateurs du groupe 1 |Value  |Description  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | 0 | Retourne tous les noms de propriété. `strQualifierName` et `pQualifierVal` sont inutilisés. |
| `WBEM_FLAG_ONLY_IF_TRUE` | 1 | Retourne uniquement les propriétés qui ont un qualificateur du nom spécifié par le `strQualifierName` paramètre. Si cet indicateur est utilisé, vous devez spécifier `strQualifierName` . |
|`WBEM_FLAG_ONLY_IF_FALSE` | 2 |  Retourne uniquement les propriétés qui n’ont pas de qualificateur du nom spécifié par le `strQualifierName` paramètre. Si cet indicateur est utilisé, vous devez spécifier `strQualifierName` . |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | 3 | Retourne uniquement les propriétés qui ont un qualificateur du nom spécifié par le `wszQualifierName` paramètre et ont également une valeur identique à celle spécifiée par la `pQualifierVal` structure. Si cet indicateur est utilisé, vous devez spécifier à la fois un `wszQualifierName` et un `pQualifierValue` . |

| Indicateurs du groupe 2 |Value  |Description  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | 0x4 | Retourne uniquement les noms des propriétés qui définissent les clés. |
|`WBEM_FLAG_REFS_ONLY` | 0x8 | Retourne uniquement les noms de propriété qui sont des références d’objet. |

| Indicateurs du groupe 3 |Value  |Description  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Retourne uniquement les noms de propriété qui appartiennent à la classe la plus dérivée. Excluez les propriétés des classes parentes. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Retourne uniquement les noms de propriété qui appartiennent aux classes parentes. |
|`WBEM_FLAG_SYSTEM_ONLY` | 0x30 | Retourne uniquement les noms des propriétés système. |
|`WBEM_FLAG_NONSYSTEM_ONLY` | 0x40 | Retourne uniquement les noms des propriétés non-système. |

La fonction alloue toujours un nouveau `SAFEARRAY` si elle retourne `WBEM_S_NO_ERROR` , et `pstrNames` est toujours définie pour pointer sur elle. Le tableau retourné peut avoir 0 élément si aucune propriété ne correspond aux filtres spécifiés. Si la fonction retourne une valeur autre que `WBM_S_NO_ERROR` , une nouvelle `SAFEARRAY` structure n’est pas retournée.

## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils. idl  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
