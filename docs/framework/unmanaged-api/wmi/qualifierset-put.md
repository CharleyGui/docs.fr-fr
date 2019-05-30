---
title: QualifierSet_Put (fonction) (référence des API non managées)
description: La fonction QualifierSet_Put écrit qualificateur nommé et sa valeur.
ms.date: 11/06/2017
api_name:
- QualifierSet_Put
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Put
helpviewer_keywords:
- QualifierSet_Put function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a11f19a9b5ebdf491b79c250da7fc5ac3d980b64
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66377865"
---
# <a name="qualifiersetput-function"></a>QualifierSet_Put (fonction)

Écrit la valeur et le qualificateur nommés. Le nouveau qualificateur remplace la valeur précédente du même nom. Si le qualificateur n’existe pas, il est créé.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT QualifierSet_Put (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LPCWSTR              wszName,
   [in] VARIANT*             pVal,
   [in] LONG                 lFlavor
);
```

## <a name="parameters"></a>Paramètres

`vFunc`\
[in] Ce paramètre n’est pas utilisé.

`ptr`\
[in] Un pointeur vers un [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.

`wszName`\
[in] Le nom du qualificateur à écrire.

`pVal`\
[in] Un pointeur vers une valide `VARIANT` qui contient le qualificateur à écrire. Ce paramètre ne peut pas être `null`.

`lFlavor`\
[in] Une des constantes suivantes qui définit les types de qualificateurs souhaitée pour ce qualificateur. La valeur par défaut est `WBEM_FLAVOR_OVERRIDABLE` (0).

|Constante  |Value  |Description  |
|---------|---------|---------|
| `WBEM_FLAVOR_OVERRIDABLE` | 0 | Le qualificateur peut être substitué dans une classe dérivée ou une instance. **Il s’agit de la valeur par défaut.** |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_INSTANCE` | 1 | Le qualificateur est propagé aux instances. |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_DERIVED_CLASS` | 2 | Le qualificateur est propagé aux classes dérivées. |
| `WBEM_FLAVOR_NOT_OVERRIDABLE` | 0x10 | Le qualificateur ne peut pas être écrasé dans une classe ou une instance dérivée. |
| `WBEM_FLAVOR_AMENDED` | 0x80 | Le qualificateur est localisé. |

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :

|Constante  |Value  |Description  |
|---------|---------|---------|
| `WBEM_E_CANNOT_BE_KEY` | 0x8004101f | Il y a une tentative non conforme pour spécifier le **clé** qualificateur sur une propriété qui ne peut pas être une clé. Les clés sont spécifiés dans la définition de classe pour un objet et ne peut pas être modifiées sur une base par instance. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Un paramètre n’est pas valide. |
| `WBEM_E_INVALID_QUALIFIER_TYPE` | 0x80041029 | Le `pVal` paramètre n’est pas un type de qualificateur conforme. |
| `WBEM_E_OVERRIDE_NOT_ALLOWED` | 0x8004101a | Il n’est pas possible d’appeler le `QualifierSet_Put` substitutions des méthodes sur le qualificateur parce que l’objet propriétaire n’autorise pas. |
| `WBEM_S_NO_ERROR` | 0 | L’appel de fonction a réussi.  |

## <a name="remarks"></a>Notes

Cette fonction encapsule un appel à la [IWbemQualifierSet::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-put) (méthode).

## <a name="requirements"></a>Configuration requise

**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).

**En-tête :** WMINet_Utils.idl

**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
