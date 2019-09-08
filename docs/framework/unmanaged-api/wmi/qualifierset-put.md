---
title: Fonction QualifierSet_Put (référence des API non managées)
description: La fonction QualifierSet_Put écrit le qualificateur nommé et sa valeur.
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
ms.openlocfilehash: 40688a0e4273233245d00fcd927f95945a43f712
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798270"
---
# <a name="qualifierset_put-function"></a>QualifierSet_Put fonction)

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
dans Ce paramètre n’est pas utilisé.

`ptr`\
dans Pointeur vers une instance [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .

`wszName`\
dans Nom du qualificateur à écrire.

`pVal`\
dans Pointeur vers un valide `VARIANT` qui contient le qualificateur à écrire. Ce paramètre ne peut pas être `null`.

`lFlavor`\
dans L’une des constantes suivantes qui définit les versions de qualificateur souhaitées pour ce qualificateur. La valeur par défaut `WBEM_FLAVOR_OVERRIDABLE` est (0).

|Constante  |Valeur  |Description  |
|---------|---------|---------|
| `WBEM_FLAVOR_OVERRIDABLE` | 0 | Le qualificateur peut être substitué dans une classe ou une instance dérivée. **Il s’agit de la valeur par défaut.** |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_INSTANCE` | 1 | Le qualificateur est propagé aux instances. |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_DERIVED_CLASS` | 2 | Le qualificateur est propagé aux classes dérivées. |
| `WBEM_FLAVOR_NOT_OVERRIDABLE` | 0x10 | Le qualificateur ne peut pas être écrasé dans une classe ou une instance dérivée. |
| `WBEM_FLAVOR_AMENDED` | 0x80 | Le qualificateur est localisé. |

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :

|Constante  |Valeur  |Description  |
|---------|---------|---------|
| `WBEM_E_CANNOT_BE_KEY` | 0x8004101f | Tentative non autorisée de spécifier le qualificateur de **clé** sur une propriété qui ne peut pas être une clé. Les clés sont spécifiées dans la définition de classe pour un objet et ne peuvent pas être modifiées pour chaque instance. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Un paramètre n’est pas valide. |
| `WBEM_E_INVALID_QUALIFIER_TYPE` | 0x80041029 | Le `pVal` paramètre n’est pas d’un type de qualificateur légal. |
| `WBEM_E_OVERRIDE_NOT_ALLOWED` | 0x8004101a | Il n’est pas possible d’appeler `QualifierSet_Put` la méthode sur le qualificateur, car l’objet propriétaire n’autorise pas les substitutions. |
| `WBEM_S_NO_ERROR` | 0 | L’appel de la fonction a réussi.  |

## <a name="remarks"></a>Notes

Cette fonction encapsule un appel à la méthode [IWbemQualifierSet ::P ut](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-put) .

## <a name="requirements"></a>Configuration requise

**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).

**En-tête :** WMINet_Utils.idl

**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performance (informations de référence sur les API non managées)](index.md)
