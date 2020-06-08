---
title: CorSymSearchPolicyAttributes, énumération
ms.date: 03/30/2017
api_name:
- CorSymSearchPolicyAttributes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSymSearchPolicyAttributes
helpviewer_keywords:
- CorSymSearchPolicyAttributes enumeration [.NET Framework debugging]
ms.assetid: 03abde84-930a-49d3-bac3-23abb34a0184
topic_type:
- apiref
ms.openlocfilehash: 8af71314cf8a24c710d3b8980c082daaf9186715
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501870"
---
# <a name="corsymsearchpolicyattributes-enumeration"></a>CorSymSearchPolicyAttributes, énumération
Spécifie la stratégie à utiliser lors de la recherche d’un lecteur de symboles. Ces constantes sont utilisées par les méthodes [ISymUnmanagedBinder2 :: GetReaderForFile2,](isymunmanagedbinder2-getreaderforfile2-method.md) et [ISymUnmanagedBinder3 :: GetReaderFromCallback,](isymunmanagedbinder3-getreaderfromcallback-method.md) .  
  
> [!IMPORTANT]
> L’ouverture d’un fichier de base de données du programme (PDB) à partir d’une source non fiable constitue un risque pour la sécurité.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorSymSearchPolicyAttributes  
{  
    AllowRegistryAccess      = 0x1,
    AllowSymbolServerAccess  = 0x2,  
    AllowOriginalPathAccess  = 0x4,     //
    AllowReferencePathAccess = 0x8  
} CorSymSearchPolicyAttributes;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`AllowRegistryAccess`|Interroge le registre pour rechercher des chemins de recherche de symboles.|  
|`AllowSymbolServerAccess`|Accède à un serveur de symboles.|  
|`AllowOriginalPathAccess`|Recherche le chemin d’accès spécifié dans le répertoire de débogage.|  
|`AllowReferencePathAccess`|Recherche le fichier PDB à l’emplacement où se trouve le fichier. exe.|  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations du magasin de symboles de diagnostics](diagnostics-symbol-store-enumerations.md)
