---
title: _CorValidateImage, fonction
ms.date: 03/30/2017
api_name:
- _CorValidateImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorValidateImage
helpviewer_keywords:
- _CorValidateImage function [.NET Framework hosting]
ms.assetid: 0117e080-05f9-4772-885d-e1847230947c
topic_type:
- apiref
ms.openlocfilehash: 3a6da0e845fa50d090cdf0808b211a5806c40961
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178216"
---
# <a name="_corvalidateimage-function"></a>_CorValidateImage, fonction
Valide les images gérées du module et avise le chargeur du système d’exploitation après qu’ils ont été chargés.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
STDAPI _CorValidateImage (
   [in] PVOID* ImageBase,  
   [in] LPCWSTR FileName  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `ImageBase`  
 [dans] Un pointeur vers l’emplacement de départ de l’image à valider en tant que code géré. L’image doit déjà être chargée dans la mémoire.  
  
 `FileName`  
 [dans] Le nom du fichier de l’image.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette fonction retourne `E_INVALIDARG`les `E_OUTOFMEMORY` `E_UNEXPECTED`valeurs `E_FAIL`standard , , et , ainsi que les valeurs suivantes.  
  
|Valeur retournée|Description|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|L’image est invalide. Cette valeur a le HRESULT 0xC00007BL.|  
|`STATUS_SUCCESS`|L’image est valide. Cette valeur a le HRESULT 0x0000000L.|  
  
## <a name="remarks"></a>Notes   
 Dans Windows XP et les versions ultérieures, le chargeur de système d’exploitation vérifie les modules gérés en examinant le bit d’annuaire COM Descriptor dans l’en-tête du format de fichier objet commun (COFF). Un bit défini indique un module géré. Si le chargeur détecte un module géré, il charge MsCorEE.dll et appelle `_CorValidateImage`, qui effectue les actions suivantes :  
  
- Confirme que l’image est un module géré valide.  
  
- Modifie le point d’entrée de l’image à un point d’entrée dans l’heure de l’exécution de la langue commune (CLR).  
  
- Pour les versions 64 bits de Windows, modifie l’image qui est en mémoire en la transformant du format PE32 au format PE32.  
  
- Retourne à la chargeuse lorsque les images du module géré sont chargées.  
  
 Pour les images exécutables, le chargeur du système d’exploitation appelle alors la fonction [_CorExeMain,](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) quel que soit le point d’entrée spécifié dans l’exécutable. Pour les images d’assemblage DLL, le chargeur appelle la [fonction _CorDllMain.](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md)  
  
 `_CorExeMain`ou `_CorDllMain` effectue les actions suivantes :  
  
- Initialise le CLR.  
  
- Localise le point d’entrée géré à partir de l’en-tête CLR de l’assemblage.  
  
- Commence l’exécution.  
  
 Le chargeur appelle la fonction [_CorImageUnloading](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md) lorsque les images du module gérée sont déchargées. Toutefois, cette fonction n’effectue aucune action; il revient juste.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** Cor.h (en)  
  
 **Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions statiques globales des métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
