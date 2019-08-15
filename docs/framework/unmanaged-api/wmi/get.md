---
title: Fonction d’extraction (référence des API non managées)
description: La fonction obtenir récupère la valeur de propriété spécifiée.
ms.date: 11/06/2017
api_name:
- Get
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Get
helpviewer_keywords:
- Get function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 265d3edbd3175eebcf6fd35be24f5b66144c960f
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69037953"
---
# <a name="get-function"></a>Get, fonction

Récupère la valeur de propriété spécifiée, si elle existe.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Get (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
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

`wszName`\
dans Nom de la propriété.

`lFlags`\
[in] Réservée. Ce paramètre doit avoir la valeur 0.

`pVal`\
à Si la fonction est correctement retournée, contient la valeur `wszName` de la propriété. Le `pval` type et la valeur corrects pour le qualificateur sont assignés à l’argument.

`pvtType`\
à Si la fonction est correctement retournée, contient une [constante de type CIM](/windows/win32/api/wbemcli/ne-wbemcli-cimtype_enumeration) qui indique le type de propriété. Sa valeur peut également être `null`. 

`plFlavor`\
à Si la fonction est correctement retournée, reçoit des informations sur l’origine de la propriété. Sa valeur peut être `null`, ou l’une des constantes WBEM_FLAVOR_TYPE suivantes définies dans le fichier d’en-tête *WbemCli. h* : 

|Constante  |Valeur  |Description  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | 0x40 | La propriété est une propriété système standard. |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | 0x20 | Pour une classe: La propriété est héritée de la classe parente. <br> Pour une instance: La propriété, bien qu’héritée de la classe parente, n’a pas été modifiée par l’instance de.  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | 0 | Pour une classe: La propriété appartient à la classe dérivée. <br> Pour une instance: La propriété est modifiée par l’instance; autrement dit, une valeur a été fournie ou un qualificateur a été ajouté ou modifié. |

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code:

|Constante  |Valeur  |Description  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Une défaillance générale s’est produite. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Un ou plusieurs paramètres ne sont pas valides. |
|`WBEM_E_NOT_FOUND` | 0x80041002 | La propriété spécifiée est introuvable. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | La mémoire disponible est insuffisante pour terminer l’opération. |
|`WBEM_S_NO_ERROR` | 0 | L’appel de la fonction a réussi.  |

## <a name="remarks"></a>Notes

Cette fonction encapsule un appel à la méthode [IWbemClassObject:: obtenir](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-get) .

La `Get` fonction peut également retourner des propriétés système.

Le `pVal` type et la valeur corrects pour le qualificateur et la fonction com [VariantInit](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantinit) sont assignés à l’argument

## <a name="requirements"></a>Configuration requise

 **Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).

 **En-tête :** WMINet_Utils.idl

 **Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performance (informations de référence sur les API non managées)](index.md)
