---
title: ICLRDebuggingLibraryProvider::ProvideLibrary, méthode
ms.date: 03/30/2017
api_name:
- ICLRDebuggingLibraryProvider.ProvideLibrary Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebuggingLibraryProvider::ProvideLibrary
helpviewer_keywords:
- ProvideLibrary method [.NET Framework debugging]
- ICLRDebuggingLibraryProvider::ProvideLibrary method [.NET Framework debugging]
ms.assetid: 86f06245-9517-49be-8d8c-ca5deaf34c02
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4a3a4e6ccb8a43f9bde5aa7a447e28c30f8d72f1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965135"
---
# <a name="iclrdebugginglibraryproviderprovidelibrary-method"></a>ICLRDebuggingLibraryProvider::ProvideLibrary, méthode
Obtient une interface de rappel de fournisseur de bibliothèque qui permet de localiser et de charger des bibliothèques de débogage spécifiques à la version common language runtime (CLR) à la demande.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ProvideLibrary(  
     [in] const WCHAR* pwszFileName,  
     [in] DWORD dwTimestamp,  
     [in] DWORD dwSizeOfImage,  
     [out] HMODULE* hModule);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pwszFilename`  
 dans Nom du module demandé.  
  
 `dwTimestamp`  
 dans Horodatage stocké dans l’en-tête de fichier COFF des fichiers PE.  
  
 `pLibraryProvider`  
 dans `SizeOfImage` Champ stocké dans l’en-tête de fichier facultatif COFF des fichiers PE.  
  
 `hModule`  
 à Handle du module demandé.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
  
## <a name="exceptions"></a>Exceptions  
  
## <a name="remarks"></a>Notes  
 `ProvideLibrary`permet au débogueur de fournir des modules nécessaires pour déboguer des fichiers CLR spécifiques tels que mscordbi. dll et mscordacwks. dll. Les handles de module doivent rester valides jusqu’à ce qu’un appel à la méthode [ICLRDebugging:: CanUnloadNow,](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md) indique qu’ils peuvent être libérés. à partir de là, il est de la responsabilité de l’appelant de libérer les handles.  
  
 Le débogueur peut utiliser n’importe quel moyen disponible pour rechercher ou acquérir le module de débogage.  
  
> [!IMPORTANT]
> Cette fonctionnalité permet à l’appelant de l’API de fournir des modules qui contiennent du code exécutable et éventuellement malveillant. Par mesure de sécurité, l’appelant ne doit pas `ProvideLibrary` utiliser pour distribuer du code qu’il n’est pas disposé à s’exécuter lui-même.  
>   
>  Si un problème de sécurité sérieux est découvert dans une bibliothèque déjà publiée, telle que mscordbi. dll ou mscordacwks. dll, le shim peut être corrigé pour reconnaître les versions erronées des fichiers. Le shim peut ensuite émettre des demandes pour les versions corrigées des fichiers et rejeter les versions erronées Si elles sont fournies en réponse à une demande. Cela peut se produire uniquement si l’utilisateur a appliqué une nouvelle version du shim. Les versions non corrigées resteront vulnérables.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug. idl, CorDebug. h  
  
 **Bibliothèque** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Débogage](../../../../docs/framework/unmanaged-api/debugging/index.md)
