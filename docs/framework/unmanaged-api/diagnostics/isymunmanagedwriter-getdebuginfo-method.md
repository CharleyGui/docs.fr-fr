---
title: ISymUnmanagedWriter::GetDebugInfo, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.GetDebugInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::GetDebugInfo
helpviewer_keywords:
- ISymUnmanagedWriter::GetDebugInfo method [.NET Framework debugging]
- GetDebugInfo method [.NET Framework debugging]
ms.assetid: dd31c210-6829-45eb-927e-cc53932638b7
topic_type:
- apiref
ms.openlocfilehash: dcab63b603d4a9a8e1430228043d2a5e597bbf4f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678290"
---
# <a name="isymunmanagedwritergetdebuginfo-method"></a>ISymUnmanagedWriter::GetDebugInfo, méthode

Retourne les informations nécessaires à un compilateur pour écrire l’entrée de répertoire de débogage dans l’en-tête de fichier exécutable portable (PE). Le writer de symbole remplit tous les champs à l’exception de `TimeDateStamp` et `PointerToRawData` . (Le compilateur est chargé de définir ces deux champs de manière appropriée.)  
  
 Un compilateur doit appeler cette méthode, émettre l’objet blob de données dans le fichier PE, définir le `PointerToRawData` champ dans le IMAGE_DEBUG_DIRECTORY de façon à ce qu’il pointe vers les données émises et écrire le IMAGE_DEBUG_DIRECTORY dans le fichier PE. Le compilateur doit également définir le `TimeDateStamp` champ pour qu’il soit égal à la valeur `TimeDateStamp` du fichier PE en cours de génération.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetDebugInfo(  
    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,  
    [in]  DWORD cData,  
    [out] DWORD *pcData,  
    [out, size_is(cData),  
        length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a>Paramètres  

 `pIDD`  
 [in, out] Pointeur vers une IMAGE_DEBUG_DIRECTORY que le writer de symbole remplira.  
  
 `cData`  
 dans `DWORD` Qui contient la taille des données de débogage.  
  
 `pcData`  
 à Pointeur vers un `DWORD` qui reçoit la taille de la mémoire tampon requise pour contenir les données de débogage.  
  
 `data`  
 à Pointeur vers une mémoire tampon qui est suffisamment grande pour contenir les données de débogage pour le magasin de symboles.  
  
## <a name="return-value"></a>Valeur renvoyée  

 S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Configuration requise  

 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedWriter, interface](isymunmanagedwriter-interface.md)
