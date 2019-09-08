---
title: IsFrameworkAssembly, fonction
ms.date: 03/30/2017
api_name:
- IsFrameworkAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IsFrameworkAssembly
helpviewer_keywords:
- IsFrameworkAssembly function [.NET Framework fusion]
ms.assetid: b0c6f19b-d4fd-4971-88f0-12ffb5793da3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 269e3702c21532f377735ba6087abb1603dde4f7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796317"
---
# <a name="isframeworkassembly-function"></a>IsFrameworkAssembly, fonction
Obtient une valeur qui indique si l’assembly spécifié est managé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT IsFrameworkAssembly (  
    [in]  LPCWSTR pwzAssemblyReference,  
    [out] LPBOOL  pbIsFrameworkAssembly,  
    [in]  LPWSTR  pwzFrameworkAssemblyIdentity,  
    [in]  LPDWORD pccSize  
 );  
```  
  
## <a name="parameters"></a>Paramètres  
 `pwzAssemblyReference`  
 dans Nom de l’assembly à vérifier.  
  
 `pbIsFrameworkAssembly`  
 à Valeur booléenne qui indique si l’assembly est managé.  
  
 `pwzFrameworkAssemblyIdentity`  
 dans Chaîne non canonique qui contient l’identité unique de l’assembly.  
  
 `pccSize`  
 [in] Taille de `pwzFrameworkAssemblyIdentity`.  
  
## <a name="remarks"></a>Notes  
 Le `pwzAssemblyReference` paramètre est un pointeur vers une chaîne de caractères qui contient le nom d’un assembly.  
  
 Si cet assembly fait partie du .NET Framework, le `pbIsFrameworkAssembly` paramètre contient une `true`valeur booléenne.  
  
 Si l’assembly nommé ne fait pas partie de la .NET Framework, ou `pwzAssemblyReference` si le paramètre ne nomme pas d' `pbIsFrameworkAssembly` assembly, `false`contient une valeur booléenne.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions statiques globales de fusion](fusion-global-static-functions.md)
