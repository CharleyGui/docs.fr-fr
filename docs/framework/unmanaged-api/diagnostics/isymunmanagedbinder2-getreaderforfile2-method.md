---
title: ISymUnmanagedBinder2::GetReaderForFile2, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder2.GetReaderForFile2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder2::GetReaderForFile2
helpviewer_keywords:
- ISymUnmanagedBinder2::GetReaderForFile2 method [.NET Framework debugging]
- GetReaderForFile2 method [.NET Framework debugging]
ms.assetid: dd92dcaf-403c-464d-a254-21594985dddd
topic_type:
- apiref
ms.openlocfilehash: e0fc6cf2a08de4a00cb8b7f98d3922df98f427c5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706968"
---
# <a name="isymunmanagedbinder2getreaderforfile2-method"></a>ISymUnmanagedBinder2::GetReaderForFile2, méthode

À partir d’une interface de métadonnées et d’un nom de fichier, retourne l’interface [ISymUnmanagedReader](isymunmanagedreader-interface.md) appropriée qui lira les symboles de débogage associés au module.  
  
 Cette méthode fournit une recherche plus complète pour le fichier de base de données du programme (PDB) que la méthode [ISymUnmanagedBinder :: GetReaderForFile,](isymunmanagedbinder-getreaderforfile-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetReaderForFile2(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a>Paramètres  

 `importer`  
 dans Pointeur vers l’interface d’importation de métadonnées.  
  
 `fileName`  
 dans Pointeur vers le nom de fichier.  
  
 `searchPath`  
 dans Pointeur vers le chemin de recherche.  
  
 `searchPolicy`  
 dans Valeur de l’énumération [CorSymSearchPolicyAttributes,](corsymsearchpolicyattributes-enumeration.md) qui spécifie la stratégie à utiliser lors de la recherche d’un lecteur de symboles.  
  
 `pRetVal`  
 à Pointeur qui a pour valeur l’interface [ISymUnmanagedReader](isymunmanagedreader-interface.md) retournée.  
  
## <a name="return-value"></a>Valeur renvoyée  

 S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Configuration requise  

 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="remarks"></a>Remarques  

 Cette version de la méthode peut rechercher le fichier PDB dans des zones autres que juste à côté du module. La stratégie de recherche peut être contrôlée en combinant [CorSymSearchPolicyAttributes,](corsymsearchpolicyattributes-enumeration.md). Par exemple, `AllowReferencePathAccess | AllowSymbolServerAccess` recherche le fichier PDB en regard du fichier exécutable et sur un serveur de symboles, mais n’interroge le registre ou n’utilise pas le chemin d’accès dans le fichier exécutable. Si le `searchPath` paramètre est fourni, la recherche sera toujours effectuée dans ces répertoires.  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedBinder2, interface](isymunmanagedbinder2-interface.md)
- [GetReaderForFile, méthode](isymunmanagedbinder-getreaderforfile-method.md)
