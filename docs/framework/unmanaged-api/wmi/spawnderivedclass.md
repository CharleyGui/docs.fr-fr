---
title: Fonction SpawnDerivedClass (référence des API non managées)
description: La fonction SpawnDerivedClass crée un nouvel objet qui dérive d’un objet.
ms.date: 11/06/2017
api_name:
- SpawnDerivedClass
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SpawnDerivedClass
helpviewer_keywords:
- SpawnDerivedClass function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 8020dd851b6773e6c76c53892c4b2bc21e4261bb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716510"
---
# <a name="spawnderivedclass-function"></a>SpawnDerivedClass, fonction

Crée un objet de classe dérivé à partir d’un objet spécifié.
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SpawnDerivedClass (
   [in] int                  vFunc,
   [in] IWbemClassObject*    ptr,
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewClass);
```  

## <a name="parameters"></a>Paramètres

`vFunc`  
dans Ce paramètre n’est pas utilisé.

`ptr`  
dans Pointeur vers une instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

`lFlags`  
[in] Réservée. Ce paramètre doit avoir la valeur 0.

`ppNewClass`  
à Reçoit le pointeur vers le nouvel objet de définition de classe. Si une erreur se produit, un nouvel objet n’est pas retourné et `ppNewClass` reste inchangé. Sa valeur ne peut pas être `null` .

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :

|Constante  |Value  |Description  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Une défaillance générale s’est produite. |
| `WBEM_E_INVALID_OPERATION` | 0x80041016 | Une opération non valide, telle que la génération d’une classe à partir d’une instance, a été demandée. |
| `WBEM_E_INCOMPLETE_CLASS` | La classe source n’a pas été complètement définie ou inscrite avec la gestion de Windows, de sorte qu’une nouvelle classe dérivée n’est pas autorisée. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | La mémoire n'est pas suffisante pour terminer cette opération. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `ppNewClass` a la valeur `null`. |
| `WBEM_S_NO_ERROR` | 0 | L’appel de la fonction a réussi.  |
  
## <a name="remarks"></a>Remarques

Cette fonction encapsule un appel à la méthode [IWbemClassObject :: SpawnDerivedClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) .

`ptr` doit être une définition de classe qui devient la classe parente de l’objet généré. L’objet retourné devient une sous-classe de l’objet actuel.

Le nouvel objet retourné `ppNewClass` automatiquement devient une sous-classe de l’objet actuel. Ce comportement ne peut pas être substitué. Il n’existe aucune autre méthode par laquelle les sous-classes (classes dérivées) peuvent être créées.

## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils. idl  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
