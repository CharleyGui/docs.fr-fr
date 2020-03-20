---
title: Fonction SpawnInstance (Référence API non gestion)
description: La fonction SpawnInstance crée une nouvelle instance d’une classe.
ms.date: 11/06/2017
api_name:
- SpawnInstance
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SpawnInstance
helpviewer_keywords:
- SpawnInstance function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: a15eb8123c1ee807444bdb4c6fe71cdccc08f434
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176719"
---
# <a name="spawninstance-function"></a>SpawnInstance, fonction
Crée une instance d’une classe.
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SpawnInstance (
   [in] int                  vFunc,
   [in] IWbemClassObject*    ptr,
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewInstance);
```  

## <a name="parameters"></a>Paramètres

`vFunc`  
[dans] Ce paramètre n’est pas utilisé.

`ptr`  
[dans] Un pointeur à une instance [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)

`lFlags`  
[in] Réservée. Ce paramètre doit être de 0.

`ppNewInstance`  
[out] Reçoit le pointeur de la nouvelle instance de la classe. Si une erreur se produit, un `ppNewInstance` nouvel objet n’est pas retourné et n’est pas modifié.

## <a name="return-value"></a>Valeur retournée

Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli.h,* ou vous pouvez les définir comme des constantes dans votre code :

|Constant  |Valeur  |Description  |
|---------|---------|---------|
| `WBEM_E_INCOMPLETE_CLASS` | 0x80041020 | `ptr`n’est pas une définition de classe valide et ne peut pas engendrer de nouveaux cas. Soit il est incomplet ou il n’a pas été enregistré auprès de Windows Management en appelant [PutClassWmi](putclasswmi.md). |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | La mémoire n'est pas suffisante pour terminer cette opération. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `ppNewClass` a la valeur `null`. |
| `WBEM_S_NO_ERROR` | 0 | L’appel de fonction a été réussi.  |
  
## <a name="remarks"></a>Notes 

Cette fonction enveloppe un appel à [l’IWbemClassObject::SpawnInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-spawninstance) méthode.

`ptr`doit être une définition de classe obtenue auprès de Windows Management. (Notez que le fait de frayer une instance à partir d’une instance est pris en charge, mais l’instance retournée est vide.) Vous utilisez ensuite cette définition de classe pour créer de nouvelles instances. Un appel à la fonction [PutInstanceWmi](putinstancewmi.md) est nécessaire si vous avez l’intention d’écrire l’instance à Windows Management.

Le nouvel objet `ppNewClass` retourné devient automatiquement une sous-classe de l’objet actuel. Ce comportement ne peut pas être remplacé. Il n’existe pas d’autre méthode par laquelle des sous-classes (classes dérivées) peuvent être créées.

## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête:** WMINet_Utils.idl  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
