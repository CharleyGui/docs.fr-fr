---
title: LockClrVersion, fonction
ms.date: 03/30/2017
api_name:
- LockClrVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- LockClrVersion
helpviewer_keywords:
- LockClrVersion function [.NET Framework hosting]
ms.assetid: 1318ee37-c43b-40eb-bbe8-88fc46453d74
topic_type:
- apiref
ms.openlocfilehash: 2ff08ec8f194ccc9e968b3a7ee017afe788f4b03
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704927"
---
# <a name="lockclrversion-function"></a>LockClrVersion, fonction

Permet à l’hôte de déterminer la version du common language runtime (CLR) qui sera utilisée dans le processus avant d’initialiser explicitement le CLR.  
  
 Cette fonction a été dépréciée dans le .NET Framework 4.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT LockClrVersion (  
    [in] FLockClrVersionCallback   hostCallback,  
    [in] FLockClrVersionCallback  *pBeginHostSetup,  
    [in] FLockClrVersionCallback  *pEndHostSetup  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `hostCallback`  
 dans Fonction à appeler par le CLR lors de l’initialisation.  
  
 `pBeginHostSetup`  
 dans Fonction à appeler par l’hôte pour informer le CLR que l’initialisation démarre.  
  
 `pEndHostSetup`  
 dans Fonction à appeler par l’hôte pour informer le CLR que l’initialisation est terminée.  
  
## <a name="return-value"></a>Valeur renvoyée  

 Cette méthode retourne des codes d’erreur COM standard, tels que définis dans WinError. h, en plus des valeurs suivantes.  
  
|Code de retour|Description|  
|-----------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|E_INVALIDARG|Un ou plusieurs arguments ont la valeur null.|  
  
## <a name="remarks"></a>Remarques  

 L’hôte appelle `LockClrVersion` avant d’initialiser le CLR. `LockClrVersion` prend trois paramètres, qui sont tous des rappels de type [FLockClrVersionCallback (](flockclrversioncallback-function-pointer.md). Ce type est défini comme suit.  
  
```cpp  
typedef HRESULT ( __stdcall *FLockClrVersionCallback ) ();  
```  
  
 Les étapes suivantes se produisent lors de l’initialisation du Runtime :  
  
1. L’hôte appelle [CorBindToRuntimeEx](corbindtoruntimeex-function.md) ou l’une des autres fonctions d’initialisation du Runtime. L’hôte peut également initialiser le runtime à l’aide de l’activation d’objet COM.  
  
2. Le runtime appelle la fonction spécifiée par le `hostCallback` paramètre.  
  
3. La fonction spécifiée par `hostCallback` effectue ensuite la séquence d’appels suivante :  
  
    - Fonction spécifiée par le `pBeginHostSetup` paramètre.  
  
    - `CorBindToRuntimeEx` (ou une autre fonction d’initialisation du Runtime).  
  
    - [ICLRRuntimeHost :: SetHostControl](iclrruntimehost-sethostcontrol-method.md).  
  
    - [ICLRRuntimeHost :: Start](iclrruntimehost-start-method.md).  
  
    - Fonction spécifiée par le `pEndHostSetup` paramètre.  
  
 Tous les appels de `pBeginHostSetup` à `pEndHostSetup` doivent se produire sur un thread ou une fibre unique, avec la même pile logique. Ce thread peut être différent du thread sur lequel `hostCallback` est appelé.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonction d'hébergement du CLR déconseillées](deprecated-clr-hosting-functions.md)
