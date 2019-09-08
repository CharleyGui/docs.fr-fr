---
title: Fonction QualifierSet_GetNames (référence des API non managées)
description: La fonction QualifierSet_GetNames récupère les noms des qualificateurs d’un objet ou d’une propriété.
ms.date: 11/06/2017
api_name:
- QualifierSet_GetNames
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_GetNames
helpviewer_keywords:
- QualifierSet_GetNames function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 266462a5393c8e26aa2bc3f2ec8ab72d4410a431
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798295"
---
# <a name="qualifierset_getnames-function"></a>QualifierSet_GetNames fonction)

Récupère les noms de tous les qualificateurs ou de certains qualificateurs disponibles à partir de la propriété ou de l’objet actuel.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT QualifierSet_GetNames (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LONG                 lFlags,
   [out] SAFEARRAY (BSTR)**  pstrNames
);
```

## <a name="parameters"></a>Paramètres

`vFunc`\
dans Ce paramètre n’est pas utilisé.

`ptr`\
dans Pointeur vers une instance [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .

`lFlags`\
dans L’un des indicateurs ou valeurs suivants qui spécifient les noms à inclure dans l’énumération.

|Constante  |Valeur  |Description  |
|---------|---------|---------|
|  | 0 | Retourne les noms de tous les qualificateurs. |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Retourne uniquement les noms des qualificateurs spécifiques à la propriété ou à l’objet actuel. <br/> Pour une propriété : Retourne uniquement les qualificateurs spécifiques à la propriété (y compris les substitutions), et non les qualificateurs propagés à partir de la définition de classe. <br/> Pour une instance : Retourne uniquement des noms de qualificateurs spécifiques à l’instance. <br/> Pour une classe : Retourne uniquement les qualificateurs spécifiques à la classe qui est dérivée.
|`WBEM_FLAG_PROPAGATED_ONLY` | 0x20 | Retourne uniquement les noms des qualificateurs propagés à partir d’un autre objet. <br/> Pour une propriété : Retourne uniquement les qualificateurs propagés à cette propriété à partir de la définition de classe, et non ceux de la propriété elle-même. <br/> Pour une instance : Retourne uniquement les qualificateurs propagés à partir de la définition de classe. <br/> Pour une classe : Retourne uniquement les noms de qualificateur hérités des classes parentes. |

`pstrNames`\
à Nouveau `SAFEARRAY` qui contient les noms demandés. Le tableau peut avoir 0 élément. Si une erreur se produit, un `SAFEARRAY` nouveau n’est pas retourné.

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :

|Constante  |Valeur  |Description  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Un paramètre n’est pas valide. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Mémoire disponible insuffisante pour commencer une nouvelle énumération. |
|`WBEM_S_NO_ERROR` | 0 | L’appel de la fonction a réussi.  |

## <a name="remarks"></a>Notes

Cette fonction encapsule un appel à la méthode [IWbemQualifierSet :: GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-getnames) .

Une fois que vous avez récupéré les noms de qualificateurs, vous pouvez accéder à chaque qualificateur par son nom en appelant la fonction [QualifierSet_Get](qualifierset-get.md) .

Il n’y a pas d’erreur pour un objet donné à avoir des qualificateurs nuls, donc le nombre `pstrNames` de chaînes dans on return peut être 0, même `WBEM_S_NO_ERROR`si la fonction retourne.

## <a name="requirements"></a>Configuration requise

**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).

**En-tête :** WMINet_Utils.idl

**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performance (informations de référence sur les API non managées)](index.md)
