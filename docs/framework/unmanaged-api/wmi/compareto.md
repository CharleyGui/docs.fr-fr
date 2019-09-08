---
title: CompareTo, fonction (référence des API non managées)
description: La fonction CompareTo compare un objet à un autre objet WMI.
ms.date: 11/06/2017
api_name:
- CompareTo
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CompareTo
helpviewer_keywords:
- CompareTo function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2ec42dff333422e247a11b4a3a5b9aed9bd316fa
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798772"
---
# <a name="compareto-function"></a>CompareTo, fonction

Compare un objet à un autre objet WMI.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CompareTo (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              flags,
   [in] IWbemClassObject* pCompareTo
);
```

## <a name="parameters"></a>Paramètres

`vFunc`\
dans Ce paramètre n’est pas utilisé.

`ptr`\
dans Pointeur vers une instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

`flags`\
dans Combinaison d’opérations de bits des indicateurs qui spécifient les caractéristiques d’objet à prendre en compte pour la comparaison. Pour plus d’informations, consultez la section [Notes](#remarks) .

`pCompareTo`\
dans Objet à comparer. `pCompareTo`doit être une instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) valide ; elle ne peut `null`pas être.

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :

|Constante  |`Value`  |Description  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Une erreur non spécifiée s’est produite. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Un paramètre n’est pas valide. |
| `WBEM_E_UNEXPECTED` | 0x8004101d | Un deuxième appel à `BeginEnumeration` a été effectué sans appel à. [`EndEnumeration`](endenumeration.md) |
| `WBEM_S_NO_ERROR` | 0 | L’appel de la fonction a réussi.  |
| `WBEM_S_DIFFERENT` | 0x40003 | Les objets sont différents. |
| `WBEM_S_SAME` | 0 | Les objets sont les mêmes en fonction des indicateurs de comparaison. |

## <a name="remarks"></a>Notes

Cette fonction encapsule un appel à la méthode [IWbemClassObject :: CompareTo](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-compareto) .

Les indicateurs qui peuvent être passés en tant `lEnumFlags` qu’argument sont définis dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code. Vous pouvez spécifier les caractéristiques individuelles impliquées dans la comparaison en spécifiant une combinaison d’opérations de bits des indicateurs suivants :

|Constante  |`Value`  |Description  |
|---------|---------|---------|
| `WBEM_FLAG_IGNORE_OBJECT_SOURCE` | 2 | Ignorez la source (le serveur et l’espace de noms à partir desquels ils proviennent). |
| `WBEM_FLAG_IGNORE_QUALIFIERS` | 1 | Ignorer tous les qualificateurs (y compris les **clés** et **dynamiques**) |
| `WBEM_FLAG_IGNORE_DEFAULT_VALUES` | 4 | Ignore les valeurs par défaut des propriétés. Cet indicateur s’applique uniquement à la comparaison des classes. |
| `WBEM_FLAG_IGNORE_FLAVOR` | 0x20 | Ignore les versions de qualificateur. Cet indicateur prend toujours en compte les qualificateurs, mais ignore les distinctions de parfum telles que les règles de propagation et les restrictions de remplacement. |
| `WBEM_FLAG_IGNORE_CASE` | 0x10 | Ignorer la casse lors de la comparaison des valeurs de chaîne. Cela s’applique à la fois aux chaînes et aux valeurs de qualificateur. La comparaison des noms de propriétés et de qualificateurs respecte toujours la casse, que cet indicateur soit défini ou non. |
| `WBEM_FLAG_IGNORE_CLASS` | 0x8 | Supposons que les objets comparés sont des instances de la même classe. Par conséquent, cet indicateur ne compare que les informations relatives à l’instance. Utilisez cet indicateur pour optimiser les performances. Si les objets ne sont pas de la même classe, les résultats ne sont pas définis. |

Vous pouvez aussi spécifier un seul indicateur composite comme suit :

|Constante  |`Value`  |Description  |
|---------|---------|---------|
|`WBEM_COMPARISON_INCLUDE_ALL` | 0 | Examinez toutes les fonctionnalités de la comparaison. |

## <a name="requirements"></a>Configuration requise

**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).

**En-tête :** WMINet_Utils.idl

**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performance (informations de référence sur les API non managées)](index.md)
