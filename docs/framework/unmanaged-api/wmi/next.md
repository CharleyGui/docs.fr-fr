---
title: Fonction Next (référence des API non managées)
description: La fonction suivante récupère la propriété suivante dans une énumération.
ms.date: 11/06/2017
api_name:
- Next
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Next
helpviewer_keywords:
- Next function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b5b456feeb1cb09e4957e470344146cf4358d8c7
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636177"
---
# <a name="next-function"></a>Fonction Next
Récupère la propriété suivante dans une énumération qui commence par un appel à [BeginEnumeration](beginenumeration.md).

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Next (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              lFlags,
   [out] BSTR*            pstrName,
   [out] VARIANT*         pVal,
   [out] CIMTYPE*         pvtType,
   [out] LONG*            plFlavor
);
```

## <a name="parameters"></a>Paramètres

`vFunc`\
[in] Ce paramètre n’est pas utilisé.

`ptr`\
[in] Un pointeur vers un [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.

`lFlags`\
[in] Réservée. Ce paramètre doit être 0.

`pstrName`\
[out] Un nouveau `BSTR` qui contient le nom de propriété. Vous pouvez définir ce paramètre sur `null` si le nom n’est pas obligatoire.

`pVal`\
[out] Un `VARIANT` renseigné avec la valeur de la propriété. Vous pouvez définir ce paramètre sur `null` si la valeur n’est pas obligatoire. Si la fonction retourne un code d’erreur, le `VARIANT` transmis à `pVal` est gauche tels quels.

`pvtType`\
[out] Un pointeur vers un `CIMTYPE` variable (un `LONG` dans lequel le type de la propriété est placé). La valeur de cette propriété peut être un `VT_NULL_VARIANT`, auquel cas il est nécessaire de déterminer le type réel de la propriété. Ce paramètre peut également être `null`.

`plFlavor`\
[out] `null`, ou une valeur qui reçoit des informations sur l’origine de la propriété. Consultez la section [Notes] pour les valeurs possibles.

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :

|Constante  |Value  |Description  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Il y a eu une défaillance générale. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Un paramètre n’est pas valide. |
| `WBEM_E_UNEXPECTED` | 0x8004101d | Il n’y avait aucun appel à la [ `BeginEnumeration` ](beginenumeration.md) (fonction). |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Pas assez de mémoire est disponible pour commencer une nouvelle énumération. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | L’appel de procédure distante entre les processus en cours et la gestion de Windows a échoué. |
| `WBEM_S_NO_ERROR` | 0 | L’appel de fonction a réussi.  |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | Il n’existe aucune autre propriété dans l’énumération. |

## <a name="remarks"></a>Notes

Cette fonction encapsule un appel à la [IWbemClassObject::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-next) (méthode).

Cette méthode retourne également les propriétés système.

Si le type sous-jacent de la propriété est un chemin d’accès de l’objet, d’une date ou heure ou un autre type spécial, le type retourné ne contient pas suffisamment d’informations. L’appelant doit examiner le `CIMTYPE` pour la propriété spécifiée déterminer si la propriété est une référence d’objet, d’une date ou heure ou un autre type spécial.

Si `plFlavor` n’est pas `null`, le `LONG` valeur reçoit des informations sur l’origine de la propriété, comme suit :

|Constante  |Value  |Description  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | 0x40 | La propriété est une propriété système standard. |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | 0x20 | Pour une classe : La propriété est héritée de la classe parente. <br> Pour une instance : La propriété, tandis que héritée de la classe parente, n’a pas été modifiée par l’instance.  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | 0 | Pour une classe : La propriété appartient à la classe dérivée. <br> Pour une instance : Cette propriété est modifiée par l’instance ; Autrement dit, une valeur a été fournie, ou un qualificateur a été ajouté ou modifié. |

## <a name="requirements"></a>Configuration requise

**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).

**En-tête :** WMINet_Utils.idl

**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
