---
title: CreateVersionStringFromModule, fonction
ms.date: 03/30/2017
api_name:
- CreateVersionStringFromModule
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- CreateVersionStringFromModule
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- CreateVersionStringFromModule function
ms.assetid: 3d2fe9bd-75ef-4364-84a6-da1e1994ac1a
topic_type:
- apiref
ms.openlocfilehash: 609d6e47c951aa104cb23084b65e98827a6851f1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789178"
---
# <a name="createversionstringfrommodule-function"></a>CreateVersionStringFromModule, fonction
Crée une chaîne de version à partir d’un chemin d’accès au Common Language Runtime (CLR) dans un processus cible.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateVersionStringFromModule (  
    [in]  DWORD      pidDebuggee,  
    [in]  LPCWSTR    szModuleName,  
    [out, size_is(cchBuffer),  
          length_is(*pdwLength)] LPWSTR Buffer,  
    [in]  DWORD      cchBuffer,  
    [out] DWORD*     pdwLength  
);  
```  
  
## <a name="parameters"></a>Parameters  
 `pidDebuggee`  
 [in] Identificateur du processus dans lequel le CLR cible est chargé.  
  
 `szModuleName`  
 [in] Chemin d’accès complet ou relatif au CLR cible chargé dans le processus.  
  
 `pBuffer`  
 [out] Mémoire tampon de retour pour stocker la chaîne de version du CLR cible.  
  
 `cchBuffer`  
 [in] Taille de `pBuffer`.  
  
 `pdwLength`  
 [out] Longueur de la chaîne de version retournée par `pBuffer`.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK  
 La chaîne de version du CLR cible a été retournée dans `pBuffer`.  
  
 E_INVALIDARG  
 `szModuleName` a la valeur null, ou `pBuffer` ou `cchBuffer` a la valeur null. `pBuffer` et `cchBuffer` doivent tous deux être null ou non null.  
  
 HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)  
 `pdwLength` est supérieur à `cchBuffer`. Il peut s'agir d'un résultat attendu si vous avez passé null pour `pBuffer` et `cchBuffer`, et interrogé la taille de la mémoire tampon nécessaire à l'aide de `pdwLength`.  
  
 HRESULT_FROM_WIN32(ERROR_MOD_NOT_FOUND)  
 `szModuleName` ne contient pas un chemin d'accès à un CLR valide dans le processus cible.  
  
 E_FAIL (ou autres codes de retour E_)  
 `pidDebuggee` ne fait pas référence à un processus valide ou à tout autre échec.  
  
## <a name="remarks"></a>Notes  
 Cette fonction accepte un processus CLR identifié par `pidDebuggee` et un chemin d'accès de chaîne spécifié par `szModuleName`. La chaîne de version est retournée dans la mémoire tampon vers laquelle pointe `pBuffer`. Cette chaîne est opaque à l'utilisateur de la fonction ; autrement dit, il n'y a aucune signification intrinsèque dans la chaîne de version elle-même. Elle est utilisée uniquement dans le contexte de cette fonction et de la [fonction CreateDebuggingInterfaceFromVersion](createdebugginginterfacefromversion-function-for-silverlight.md).  
  
 Cette fonction doit être appelée deux fois. Quand vous appelez pour la première fois, passez la valeur null pour `pBuffer` et `cchBuffer`. Quand vous procédez ainsi, la taille de la mémoire tampon nécessaire pour `pBuffer` est retournée dans `pdwLength`. Vous pouvez ensuite appeler la fonction une seconde fois et passer la mémoire tampon dans `pBuffer` et sa taille dans `cchBuffer`.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** dbgshim. h  
  
 **Bibliothèque :** dbgshim. dll  
  
 **Versions de .NET Framework :** 3,5 SP1
