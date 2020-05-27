---
title: METAHOST_POLICY_FLAGS, énumération
ms.date: 03/30/2017
api_name:
- METAHOST_POLICY_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- METAHOST_POLICY_FLAGS
helpviewer_keywords:
- METAHOST_POLICY_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 3bb4b526-0118-42e2-ba59-c95648528ce9
topic_type:
- apiref
ms.openlocfilehash: bb40ed65a2e34f1bf293e4c4c842d7db63d2eaa5
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008441"
---
# <a name="metahost_policy_flags-enumeration"></a>METAHOST_POLICY_FLAGS, énumération
Fournit des stratégies de liaison communes à la plupart des hôtes de Runtime. Cette énumération est utilisée par la méthode [ICLRMetaHostPolicy :: GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    METAHOST_POLICY_HIGHCOMPAT              = 0x00,  
    METAHOST_POLICY_APPLY_UPGRADE_POLICY    = 0x08,  
    METAHOST_POLICY_EMULATE_EXE_LAUNCH      = 0x10,  
    METAHOST_POLICY_SHOW_ERROR_DIALOG       = 0x20,  
    METAHOST_POLICY_USE_PROCESS_IMAGE_PATH  = 0x40,  
    METAHOST_POLICY_ENSURE_SKU_SUPPORTED    = 0x80,  
    METAHOST_POLICY_IGNORE_ERROR_MODE       = 0x1000  
  
} METAHOST_POLICY_FLAGS;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`METAHOST_POLICY_HIGHCOMPAT`|Définit la stratégie de haute compatibilité, qui ne tient pas compte des common language runtime (CLR) chargés dans le processus actuel. Au lieu de cela, il considère uniquement les CLR installés et les préférences du composant, telles qu’elles sont dérivées du fichier d’assembly lui-même, de la version intégrée déclarée ou du fichier de configuration.|  
|`METAHOST_POLICY_APPLY_UPGRADE_POLICY`|Applique la stratégie de mise à niveau au résultat de liaison de version lorsqu’une correspondance exacte est introuvable, en fonction du contenu de HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft \\ . NETFramework\Policy\Upgrades. Cela a le même effet que [RUNTIME_INFO_UPGRADE_VERSION](runtime-info-flags-enumeration.md).|  
|`METAHOST_POLICY_EMULATE_EXE_LAUNCH`|Les résultats de liaison sont retournés comme si l’image fournie à l’appel avait été lancée dans un nouveau processus. Actuellement, `GetRequestedRuntime` ignore l’ensemble des runtimes et des liaisons chargeable par rapport au jeu de runtimes installés. Cet indicateur permet à un hôte de déterminer à quel Runtime est lié un EXE lorsqu’il est lancé.|  
|`METAHOST_POLICY_SHOW_ERROR_DIALOG`|Une boîte de dialogue d’erreur s’affiche si `GetRequestedRuntime` ne parvient pas à trouver un Runtime compatible avec les paramètres d’entrée. À partir de la .NET Framework 4,5, cette boîte de dialogue d’erreur peut prendre la forme d’une boîte de dialogue de fonctionnalité Windows qui vous demande si l’utilisateur souhaite activer la fonctionnalité appropriée.|  
|`METAHOST_POLICY_USE_PROCESS_IMAGE_PATH`|`GetRequestedRuntime`utilise l’image de processus (et tout fichier de configuration correspondant) comme entrée supplémentaire dans le processus de liaison. Par défaut, `GetRequestedRuntime` ne revient pas au chemin d’accès de l’image de processus (en général, le fichier exe qui a été utilisé pour lancer le processus) lors de la détermination du runtime à lier.|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|`GetRequestedRuntime`doit vérifier si la référence (SKU) appropriée est installée quand aucune information n’est disponible dans le fichier de configuration. Cela permet aux applications qui n’ont pas de fichiers de configuration d’échouer correctement sur des références plus petites que l’installation par défaut de la .NET Framework. Par défaut, `GetRequestedRuntime` ne vérifie pas si la référence SKU appropriée est installée, sauf si l’attribut sku est spécifié dans l’élément fichier de configuration `<supportedRuntime />` .|  
|`METAHOST_POLICY_IGNORE_ERROR_MODE`|`GetRequestedRuntime`doit ignorer SEM_FAILCRITICALERRORS (qui est défini en appelant la fonction [SetErrorMode](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode) ) et afficher la boîte de dialogue d’erreur. Par défaut, SEM_FAILCRITICALERRORS supprime la boîte de dialogue d’erreur. Elle a peut-être été héritée d’un autre processus et l’erreur silencieuse peut ne pas être souhaitable dans votre scénario.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Metahost. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations d'hébergement](hosting-enumerations.md)
- [GetRequestedRuntime, méthode](iclrmetahostpolicy-getrequestedruntime-method.md)
