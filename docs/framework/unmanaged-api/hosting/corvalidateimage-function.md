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
ms.openlocfilehash: 426b39aa3d1ada5ae44565a742b70681a7bcf6d3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493433"
---
# <a name="_corvalidateimage-function"></a>_CorValidateImage, fonction
Valide les images de modules managés et notifie le chargeur du système d’exploitation après qu’elles ont été chargées.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
STDAPI _CorValidateImage (
   [in] PVOID* ImageBase,  
   [in] LPCWSTR FileName  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `ImageBase`  
 dans Pointeur vers l’emplacement de départ de l’image à valider comme code managé. L’image doit déjà être chargée dans la mémoire.  
  
 `FileName`  
 dans Nom de fichier de l’image.  
  
## <a name="return-value"></a>Valeur renvoyée  
 Cette fonction retourne les valeurs standard `E_INVALIDARG` , `E_OUTOFMEMORY` , `E_UNEXPECTED` et `E_FAIL` , ainsi que les valeurs suivantes.  
  
|Valeur de retour|Description|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|L’image n’est pas valide. Cette valeur a le HRESULT 0xC000007BL.|  
|`STATUS_SUCCESS`|L’image est valide. Cette valeur a le HRESULT 0x00000000L.|  
  
## <a name="remarks"></a>Remarques  
 Dans Windows XP et versions ultérieures, le chargeur du système d’exploitation recherche les modules managés en examinant le bit du répertoire du descripteur COM dans l’en-tête COFF (Common Object File Format). Un bit défini indique un module managé. Si le chargeur détecte un module managé, il charge MsCorEE. dll et appelle `_CorValidateImage` , qui effectue les actions suivantes :  
  
- Confirme que l’image est un module managé valide.  
  
- Modifie le point d’entrée dans l’image en point d’entrée dans le common language runtime (CLR).  
  
- Pour les versions 64 bits de Windows, modifie l’image en mémoire en la transformant de PE32 en format PE32 +.  
  
- Retourne au chargeur lorsque les images de modules managés sont chargées.  
  
 Pour les images exécutables, le chargeur du système d’exploitation appelle ensuite la fonction [_CorExeMain](corexemain-function.md) , quel que soit le point d’entrée spécifié dans le fichier exécutable. Pour les images d’assembly DLL, le chargeur appelle la fonction [_CorDllMain](cordllmain-function.md) .  
  
 `_CorExeMain`ou `_CorDllMain` effectue les actions suivantes :  
  
- Initialise le CLR.  
  
- Localise le point d’entrée managé dans l’en-tête CLR de l’assembly.  
  
- Commence l’exécution.  
  
 Le chargeur appelle la fonction [_CorImageUnloading](corimageunloading-function.md) lorsque les images de modules managés sont déchargées. Toutefois, cette fonction n’exécute aucune action ; elle retourne simplement.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions statiques globales des métadonnées](../metadata/metadata-global-static-functions.md)
