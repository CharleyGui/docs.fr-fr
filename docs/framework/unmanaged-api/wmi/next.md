---
title: Fonction Next (référence des API non managées)
description: La fonction Next récupère la propriété Next dans une énumération.
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
ms.openlocfilehash: c2a7fae32e82caae40a95bfdad10fa78082988ef
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726781"
---
# <a name="next-function"></a>Next, fonction

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
dans Ce paramètre n’est pas utilisé.

`ptr`\
dans Pointeur vers une instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

`lFlags`\
[in] Réservée. Ce paramètre doit avoir la valeur 0.

`pstrName`\
à Nouveau `BSTR` qui contient le nom de la propriété. Vous pouvez définir ce paramètre sur `null` si le nom n’est pas obligatoire.

`pVal`\
à `VARIANT` Rempli avec la valeur de la propriété. Vous pouvez définir ce paramètre sur `null` si la valeur n’est pas requise. Si la fonction retourne un code d’erreur, le `VARIANT` passé à `pVal` n’est pas modifié.

`pvtType`\
à Pointeur vers une `CIMTYPE` variable ( `LONG` dans laquelle le type de la propriété est placé). La valeur de cette propriété peut être `VT_NULL_VARIANT` , auquel cas il est nécessaire de déterminer le type réel de la propriété. Ce paramètre peut également être `null` .

`plFlavor`\
[out] `null` , ou une valeur qui reçoit des informations sur l’origine de la propriété. Pour connaître les valeurs possibles, consultez la section [remarques].

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :

|Constante  |Value  |Description  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Une défaillance générale s’est produite. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Un paramètre n’est pas valide. |
| `WBEM_E_UNEXPECTED` | 0x8004101d | Aucun appel à la [`BeginEnumeration`](beginenumeration.md) fonction. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Mémoire disponible insuffisante pour commencer une nouvelle énumération. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | L’appel de procédure distante entre le processus en cours et l’administration de Windows a échoué. |
| `WBEM_S_NO_ERROR` | 0 | L’appel de la fonction a réussi.  |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | Il n’y a plus de propriétés dans l’énumération. |

## <a name="remarks"></a>Remarques

Cette fonction encapsule un appel à la méthode [IWbemClassObject :: Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-next) .

Cette méthode retourne également les propriétés système.

Si le type sous-jacent de la propriété est un chemin d’accès d’objet, une date ou une heure, ou un autre type spécial, le type retourné ne contient pas suffisamment d’informations. L’appelant doit examiner le `CIMTYPE` pour la propriété spécifiée afin de déterminer si la propriété est une référence d’objet, une date ou une heure, ou un autre type spécial.

Si `plFlavor` n’est pas `null` , la `LONG` valeur reçoit des informations sur l’origine de la propriété, comme suit :

|Constante  |Value  |Description  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | 0x40 | La propriété est une propriété système standard. |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | 0x20 | Pour une classe : la propriété est héritée de la classe parente. <br> Pour une instance : la propriété, alors qu’elle est héritée de la classe parente, n’a pas été modifiée par l’instance.  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | 0 | Pour une classe : la propriété appartient à la classe dérivée. <br> Pour une instance : la propriété est modifiée par l’instance ; autrement dit, une valeur a été fournie ou un qualificateur a été ajouté ou modifié. |

## <a name="requirements"></a>Configuration requise

**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).

**En-tête :** WMINet_Utils. idl

**Versions de .NET Framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
