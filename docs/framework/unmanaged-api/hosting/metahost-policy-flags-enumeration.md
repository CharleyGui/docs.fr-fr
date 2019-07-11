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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d35bd5f8aaa2dc0df0044671414a5a936fed24d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781053"
---
# <a name="metahostpolicyflags-enumeration"></a><span data-ttu-id="17444-102">METAHOST_POLICY_FLAGS, énumération</span><span class="sxs-lookup"><span data-stu-id="17444-102">METAHOST_POLICY_FLAGS Enumeration</span></span>
<span data-ttu-id="17444-103">Fournit des stratégies de liaison qui sont communes à la plupart des hôtes de runtime.</span><span class="sxs-lookup"><span data-stu-id="17444-103">Provides binding policies that are common to most runtime hosts.</span></span> <span data-ttu-id="17444-104">Cette énumération est utilisée par le [ICLRMetaHostPolicy::GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="17444-104">This enumeration is used by the [ICLRMetaHostPolicy::GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17444-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="17444-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="17444-106">Membres</span><span class="sxs-lookup"><span data-stu-id="17444-106">Members</span></span>  
  
|<span data-ttu-id="17444-107">Membre</span><span class="sxs-lookup"><span data-stu-id="17444-107">Member</span></span>|<span data-ttu-id="17444-108">Description</span><span class="sxs-lookup"><span data-stu-id="17444-108">Description</span></span>|  
|------------|-----------------|  
|`METAHOST_POLICY_HIGHCOMPAT`|<span data-ttu-id="17444-109">Définit la stratégie haute compatibilité, qui ne tient pas compte de n’importe quel common language runtime (CLR) qui est chargé dans le processus en cours.</span><span class="sxs-lookup"><span data-stu-id="17444-109">Defines the high-compatibility policy, which does not consider any common language runtime (CLR) that is loaded into the current process.</span></span> <span data-ttu-id="17444-110">Au lieu de cela, il ne considère que les CLR installés et les préférences du composant, comme dérivé le fichier d’assembly, la version de génération déclarée ou le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="17444-110">Instead, it considers only the installed CLRs and the preferences of the component, as derived from the assembly file itself, the declared built-against version, or the configuration file.</span></span>|  
|`METAHOST_POLICY_APPLY_UPGRADE_POLICY`|<span data-ttu-id="17444-111">Applique la stratégie de mise à niveau pour le résultat de liaison de version lorsqu’une correspondance exacte est introuvable, en fonction du contenu de HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework\Policy\Upgrades.</span><span class="sxs-lookup"><span data-stu-id="17444-111">Applies upgrade policy to the version bind result when an exact match is not found, based on the contents of HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\Policy\Upgrades.</span></span> <span data-ttu-id="17444-112">Cela a le même effet que [RUNTIME_INFO_UPGRADE_VERSION](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="17444-112">This has the same effect as [RUNTIME_INFO_UPGRADE_VERSION](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md).</span></span>|  
|`METAHOST_POLICY_EMULATE_EXE_LAUNCH`|<span data-ttu-id="17444-113">Résultats de la liaison sont retournés comme si l’image fournie à l’appel était lancée dans un nouveau processus.</span><span class="sxs-lookup"><span data-stu-id="17444-113">Binding results are returned as if the image provided to the call were launched in a new process.</span></span> <span data-ttu-id="17444-114">Actuellement, `GetRequestedRuntime` ignore l’ensemble des runtimes chargeables et lie par rapport à l’ensemble des runtimes installés.</span><span class="sxs-lookup"><span data-stu-id="17444-114">Currently, `GetRequestedRuntime` ignores the set of loadable runtimes and binds against the set of installed runtimes.</span></span> <span data-ttu-id="17444-115">Cet indicateur permet à un hôte de déterminer à quelle exécution un EXE sera lié lorsqu’elle est lancée.</span><span class="sxs-lookup"><span data-stu-id="17444-115">This flag allows a host to determine which runtime an EXE will bind to when it is launched.</span></span>|  
|`METAHOST_POLICY_SHOW_ERROR_DIALOG`|<span data-ttu-id="17444-116">Une boîte de dialogue d’erreur s’affiche si `GetRequestedRuntime` ne peut pas trouver un runtime qui est compatible avec les paramètres d’entrée.</span><span class="sxs-lookup"><span data-stu-id="17444-116">An error dialog box is displayed if `GetRequestedRuntime` is unable to find a runtime that is compatible with the input parameters.</span></span> <span data-ttu-id="17444-117">À compter de .NET Framework 4.5, cette boîte de dialogue d’erreur peut prendre la forme d’une boîte de dialogue de fonctionnalité de Windows qui vous demande si l’utilisateur souhaite activer la fonctionnalité appropriée.</span><span class="sxs-lookup"><span data-stu-id="17444-117">Beginning with the .NET Framework 4.5, this error dialog box can take the form of a Windows feature dialog box that asks whether the user would like to enable the appropriate feature.</span></span>|  
|`METAHOST_POLICY_USE_PROCESS_IMAGE_PATH`|<span data-ttu-id="17444-118">`GetRequestedRuntime` utilise l’image du processus (et tout fichier de configuration correspondant) comme entrée supplémentaire au processus de liaison.</span><span class="sxs-lookup"><span data-stu-id="17444-118">`GetRequestedRuntime` uses the process image (and any corresponding configuration file) as additional input to the binding process.</span></span> <span data-ttu-id="17444-119">Par défaut, `GetRequestedRuntime` ne tombe pas dans le chemin d’image de processus (en général, l’EXE qui a été utilisé pour lancer le processus) lors de la détermination du runtime à lier.</span><span class="sxs-lookup"><span data-stu-id="17444-119">By default, `GetRequestedRuntime` does not fall back to the process image path (typically, the EXE that was used to launch the process) when determining the runtime to bind to.</span></span>|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|<span data-ttu-id="17444-120">`GetRequestedRuntime` doit vérifier si la référence SKU appropriée est installé lorsque aucune information n’est disponible dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="17444-120">`GetRequestedRuntime` must check whether the appropriate SKU is installed when no information is available in the configuration file.</span></span> <span data-ttu-id="17444-121">Cela permet aux applications qui n’ont pas de fichiers de configuration d’échouer correctement sur des références plus petites que l’installation par défaut du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="17444-121">This allows applications that do not have configuration files to fail gracefully on smaller SKUs than the default installation of the .NET Framework.</span></span> <span data-ttu-id="17444-122">Par défaut, `GetRequestedRuntime` ne vérifie pas si la référence SKU appropriée est installé, sauf si l’attribut de référence (SKU) est spécifié dans le fichier de configuration `<supportedRuntime />` élément.</span><span class="sxs-lookup"><span data-stu-id="17444-122">By default, `GetRequestedRuntime` does not check whether the appropriate SKU is installed unless the SKU attribute is specified in the configuration file `<supportedRuntime />` element.</span></span>|  
|`METAHOST_POLICY_IGNORE_ERROR_MODE`|<span data-ttu-id="17444-123">`GetRequestedRuntime` doit ignorer SEM_FAILCRITICALERRORS (qui est défini en appelant le [SetErrorMode](https://go.microsoft.com/fwlink/p/?LinkId=255242) fonction) et afficher la boîte de dialogue d’erreur.</span><span class="sxs-lookup"><span data-stu-id="17444-123">`GetRequestedRuntime` should ignore SEM_FAILCRITICALERRORS (which is set by calling the [SetErrorMode](https://go.microsoft.com/fwlink/p/?LinkId=255242) function), and show the error dialog box.</span></span> <span data-ttu-id="17444-124">Par défaut, SEM_FAILCRITICALERRORS supprime la boîte de dialogue d’erreur.</span><span class="sxs-lookup"><span data-stu-id="17444-124">By default, SEM_FAILCRITICALERRORS suppresses the error dialog box.</span></span> <span data-ttu-id="17444-125">Il peut avoir hérité à partir d’un autre processus, et l’erreur en mode silencieux peut être indésirable dans votre scénario.</span><span class="sxs-lookup"><span data-stu-id="17444-125">It may have been inherited from another process, and the silent error may be undesirable in your scenario.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17444-126">Notes</span><span class="sxs-lookup"><span data-stu-id="17444-126">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17444-127">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="17444-127">Requirements</span></span>  
 <span data-ttu-id="17444-128">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17444-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17444-129">**En-tête :** Metahost.h</span><span class="sxs-lookup"><span data-stu-id="17444-129">**Header:** Metahost.h</span></span>  
  
 <span data-ttu-id="17444-130">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="17444-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="17444-131">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17444-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17444-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="17444-132">See also</span></span>

- [<span data-ttu-id="17444-133">Énumérations d’hébergement</span><span class="sxs-lookup"><span data-stu-id="17444-133">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
- [<span data-ttu-id="17444-134">GetRequestedRuntime, méthode</span><span class="sxs-lookup"><span data-stu-id="17444-134">GetRequestedRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)
