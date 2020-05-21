---
title: ICLRStrongName, interface
ms.date: 03/30/2017
api_name:
- ICLRStrongName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName
helpviewer_keywords:
- ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 2fac66fd-6b3b-4dbd-8baf-86038bd85526
topic_type:
- apiref
ms.openlocfilehash: 04260429dd69f5ba1d6a94b6628979341d12b9e8
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762074"
---
# <a name="iclrstrongname-interface"></a>ICLRStrongName, interface
Fournit des fonctions statiques globales de base pour la signature d’assemblys avec des noms forts. Toutes les `ICLRStrongName` méthodes retournent des valeurs HRESULT com standard.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetHashFromAssemblyFile, méthode](iclrstrongname-gethashfromassemblyfile-method.md)|Obtient un hachage du fichier d’assembly spécifié, à l’aide de l’algorithme de hachage spécifié.|  
|[GetHashFromAssemblyFileW, méthode](iclrstrongname-gethashfromassemblyfilew-method.md)|Obtient un hachage du fichier d’assembly spécifié sous forme de chaîne Unicode, à l’aide de l’algorithme de hachage spécifié.|  
|[GetHashFromBlob, méthode](iclrstrongname-gethashfromblob-method.md)|Obtient un hachage de l’assembly à l’adresse mémoire spécifiée, à l’aide de l’algorithme de hachage spécifié.|  
|[GetHashFromFile, méthode](iclrstrongname-gethashfromfile-method.md)|Génère un hachage sur le contenu du fichier spécifié.|  
|[GetHashFromFileW, méthode](iclrstrongname-gethashfromfilew-method.md)|Génère un hachage sur le contenu du fichier spécifié par une chaîne Unicode.|  
|[GetHashFromHandle, méthode](iclrstrongname-gethashfromhandle-method.md)|Génère un hachage sur le contenu du fichier avec le handle de fichier spécifié, à l’aide de l’algorithme de hachage spécifié.|  
|[StrongNameCompareAssemblies, méthode](iclrstrongname-strongnamecompareassemblies-method.md)|Détermine si deux assemblys diffèrent uniquement par leurs signatures avec nom fort.|  
|[StrongNameFreeBuffer, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)|Libère de la mémoire qui a été allouée avec un appel précédent à une méthode de nom fort, telle que [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md), [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)ou [StrongNameSignatureGeneration](iclrstrongname-strongnamesignaturegeneration-method.md).|  
|[StrongNameGetBlob, méthode](iclrstrongname-strongnamegetblob-method.md)|Remplit la mémoire tampon spécifiée avec la représentation binaire du fichier exécutable à l’adresse spécifiée.|  
|[StrongNameGetBlobFromImage, méthode](iclrstrongname-strongnamegetblobfromimage-method.md)|Obtient une représentation binaire de l’image de l’assembly à l’adresse mémoire spécifiée.|  
|[StrongNameGetPublicKey, méthode](iclrstrongname-strongnamegetpublickey-method.md)|Obtient la clé publique à partir d’une paire de clés publique/privée.|  
|[StrongNameHashSize, méthode](iclrstrongname-strongnamehashsize-method.md)|Obtient la taille de mémoire tampon requise pour un hachage, à l’aide de l’algorithme de hachage spécifié.|  
|[StrongNameKeyDelete, méthode](iclrstrongname-strongnamekeydelete-method.md)|Supprime le conteneur de clé spécifié.|  
|[StrongNameKeyGen, méthode](iclrstrongname-strongnamekeygen-method.md)|Crée une nouvelle paire de clés publique/privée pour une utilisation de nom fort.|  
|[StrongNameKeyGenEx, méthode](iclrstrongname-strongnamekeygenex-method.md)|Génère une nouvelle paire de clés publique/privée avec la taille de clé spécifiée pour une utilisation de nom fort.|  
|[StrongNameKeyInstall, méthode](iclrstrongname-strongnamekeyinstall-method.md)|Importe une paire de clés publique/privée dans un conteneur.|  
|[StrongNameSignatureGeneration, méthode](iclrstrongname-strongnamesignaturegeneration-method.md)|Génère une signature de nom fort pour l’assembly spécifié.|  
|[StrongNameSignatureGenerationEx, méthode](iclrstrongname-strongnamesignaturegenerationex-method.md)|Génère une signature de nom fort pour l’assembly spécifié, en fonction des indicateurs spécifiés.|  
|[StrongNameSignatureSize, méthode](iclrstrongname-strongnamesignaturesize-method.md)|Retourne la taille de la signature de nom fort.|  
|[StrongNameSignatureVerification, méthode](iclrstrongname-strongnamesignatureverification-method.md)|Obtient une valeur indiquant si le manifeste d’assembly au chemin fourni contient une signature de nom fort, qui est vérifiée en fonction des indicateurs spécifiés.|  
|[StrongNameSignatureVerificationEx, méthode](iclrstrongname-strongnamesignatureverificationex-method.md)|Obtient une valeur indiquant si le manifeste d’assembly au chemin fourni contient une signature de nom fort.|  
|[StrongNameSignatureVerificationFromImage, méthode](iclrstrongname-strongnamesignatureverificationfromimage-method.md)|Vérifie qu’un assembly qui a déjà été mappé en mémoire est valide pour la clé publique associée.|  
|[StrongNameTokenFromAssembly, méthode](iclrstrongname-strongnametokenfromassembly-method.md)|Crée un jeton de nom fort à partir du fichier d’assembly spécifié.|  
|[StrongNameTokenFromAssembly, méthode](iclrstrongname-strongnametokenfromassemblyex-method.md)|Crée un jeton de nom fort à partir du fichier d’assembly spécifié et retourne la clé publique.|  
|[StrongNameTokenFromPublicKey, méthode](iclrstrongname-strongnametokenfrompublickey-method.md)|Obtient un jeton représentant une clé publique.|  
  
## <a name="remarks"></a>Notes  
 Vous pouvez récupérer une instance du `ICLRStrongName` en appelant la méthode [ICLRRuntimeInfo :: GetInterface](iclrruntimeinfo-getinterface-method.md) à l’aide `CLSID_CLRStrongName` de et `IID_ICLRStrongName` en tant que paramètres.  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Metahost. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces d'hébergement](hosting-interfaces.md)
- [Hébergement](index.md)
