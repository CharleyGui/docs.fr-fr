---
title: SpawnInstance (fonction) (référence des API non managées)
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 97a3ab62cda82526a7ad8b8e5d985d9fce7d6f07
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783068"
---
# <a name="spawninstance-function"></a>SpawnInstance (fonction)
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
[in] Ce paramètre n’est pas utilisé.

`ptr`  
[in] Un pointeur vers un [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.

`lFlags`  
[in] Réservée. Ce paramètre doit être 0.

`ppNewInstance`  
[out] Reçoit le pointeur vers la nouvelle instance de la classe. Si une erreur se produit, un nouvel objet n’est pas retournée, et `ppNewInstance` est gauche tels quels.

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :

|Constante  |Valeur  |Description  |
|---------|---------|---------|
| `WBEM_E_INCOMPLETE_CLASS` | 0x80041020 | `ptr` n’est pas une définition de classe valide et ne peut pas générer de nouvelles instances. Soit il est incomplet, soit il n’a pas été inscrit avec la gestion de Windows en appelant [PutClassWmi](putclasswmi.md). |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Mémoire est insuffisante pour terminer l’opération. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `ppNewClass` a la valeur `null`. |
| `WBEM_S_NO_ERROR` | 0 | L’appel de fonction a réussi.  |
  
## <a name="remarks"></a>Notes

Cette fonction encapsule un appel à la [IWbemClassObject::SpawnInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-spawninstance) (méthode).

`ptr` doit être une définition de classe obtenue à partir de la gestion de Windows. (Notez que lors de la génération une instance d’une instance est prise en charge, mais l’instance retournée est vide.) Vous utilisez ensuite cette définition de classe pour créer des instances. Un appel à la [PutInstanceWmi](putinstancewmi.md) fonction est nécessaire si vous avez l’intention d’écrire l’instance à la gestion de Windows.

Le nouvel objet retourné dans `ppNewClass` devient automatiquement une sous-classe de l’objet actuel. Ce comportement ne peut pas être remplacé. Il n’existe aucune autre méthode par laquelle les sous-classes (classes dérivées) peuvent être créés.

## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils.idl  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
