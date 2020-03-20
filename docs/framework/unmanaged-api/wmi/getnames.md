---
title: Fonction GetNames (référence API non gestion)
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
ms.openlocfilehash: 449f0ce9c291d4bbcad4947214e56ff46f55beed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174951"
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
[dans] Ce paramètre n’est pas utilisé.

`ptr`  
[dans] Un pointeur à une instance [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)

`wszQualifierName`  
[dans] Un pointeur `LPCWSTR` à un valide qui spécifie un nom qualificatif qui fonctionne dans le cadre d’un filtre. Pour plus d’informations, consultez la section [Remarques.](#remarks) Ce paramètre peut être `null`.

`lFlags`  
[dans] Une combinaison de champs de bits. Pour plus d’informations, consultez la section [Remarques.](#remarks)

`pQualifierValue`[dans] Un pointeur `VARIANT` vers une structure valide paralysée à une valeur de filtre. Ce paramètre peut être `null`.

`pstrNames`  
[out] Une `SAFEARRAY` structure qui contient des noms de propriété. À l’entrée, ce paramètre `null`doit toujours être un pointeur à . Consultez la section [Remarques](#remarks) pour plus d’informations.

## <a name="return-value"></a>Valeur retournée

Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli.h,* ou vous pouvez les définir comme des constantes dans votre code :

|Constant  |Valeur  |Description  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Il y a eu un échec général. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Un ou plusieurs paramètres ne sont pas valides, ou une combinaison incorrecte de drapeaux et de paramètres a été spécifiée. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | La mémoire n'est pas suffisante pour terminer cette opération. |
|`WBEM_S_NO_ERROR` | 0 | L’appel de fonction a été réussi.  |
  
## <a name="remarks"></a>Notes 

Cette fonction enveloppe un appel à [l’IWbemClassObject::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) méthode.

Les personnes nommées sont contrôlées par une combinaison de drapeaux et de paramètres. Par exemple, la fonction peut retourner les noms de toutes les propriétés ou seulement les noms des propriétés clés.  Le filtre principal est `lFlags` spécifié dans le paramètre, et les autres paramètres varient en fonction de lui.

Les valeurs `lFlags` du drapeau sont des champs bits

Les drapeaux qui peuvent `lEnumFlags` être passés comme l’argument sont des champs bit qui sont définis dans le fichier *d’en-tête WbemCli.h,* ou vous pouvez les définir comme des constantes dans votre code.  Vous pouvez combiner un drapeau de chaque groupe avec n’importe quel drapeau de n’importe quel autre groupe. Cependant, les drapeaux du même groupe s’excluent mutuellement.

| Drapeaux du groupe 1 |Valeur  |Description  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | 0 | Retournez tous les noms de propriété. `strQualifierName`et `pQualifierVal` sont inutilisés. |
| `WBEM_FLAG_ONLY_IF_TRUE` | 1 | Retournez uniquement les propriétés qui ont `strQualifierName` un qualificatif du nom spécifié par le paramètre. Si ce drapeau est utilisé, vous devez spécifier `strQualifierName`. |
|`WBEM_FLAG_ONLY_IF_FALSE` | 2 |  Retournez uniquement les propriétés qui n’ont `strQualifierName` pas de qualification du nom spécifiée par le paramètre. Si ce drapeau est utilisé, vous devez spécifier `strQualifierName`. |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | 3 | Retournez uniquement les propriétés qui ont `wszQualifierName` un qualificatif du nom `pQualifierVal` spécifié par le paramètre et ont également une valeur identique à celle spécifiée par la structure. Si ce drapeau est utilisé, `wszQualifierName` vous `pQualifierValue`devez spécifier à la fois un et un . |

| Drapeaux du groupe 2 |Valeur  |Description  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | 0x4 | Ne retournez que les noms des propriétés qui définissent les clés. |
|`WBEM_FLAG_REFS_ONLY` | 0x8 | Ne retournez que les noms de propriété qui sont des références d’objet. |

| Drapeaux du groupe 3 |Valeur  |Description  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Ne retournez que les noms de propriété qui appartiennent à la classe la plus dérivée. Exclure les propriétés des classes parentales. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Ne retournez que les noms de propriété qui appartiennent aux classes de parents. |
|`WBEM_FLAG_SYSTEM_ONLY` | 0x30 | Ne retournez que les noms des propriétés du système. |
|`WBEM_FLAG_NONSYSTEM_ONLY` | 0x40 | Ne retournez que les noms des propriétés non système. |

La fonction alloue `SAFEARRAY` toujours `WBEM_S_NO_ERROR`un `pstrNames` nouveau si elle revient, et est toujours mis à lui pointer du point. Le tableau retourné peut avoir 0 éléments si aucune propriété ne correspond aux filtres spécifiés. Si la fonction retourne `WBM_S_NO_ERROR`une valeur `SAFEARRAY` autre que , une nouvelle structure n’est pas retournée.

## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête:** WMINet_Utils.idl  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
