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
# <a name="metahost_policy_flags-enumeration"></a><span data-ttu-id="5ca06-102">METAHOST_POLICY_FLAGS, énumération</span><span class="sxs-lookup"><span data-stu-id="5ca06-102">METAHOST_POLICY_FLAGS Enumeration</span></span>
<span data-ttu-id="5ca06-103">Fournit des stratégies de liaison communes à la plupart des hôtes de Runtime.</span><span class="sxs-lookup"><span data-stu-id="5ca06-103">Provides binding policies that are common to most runtime hosts.</span></span> <span data-ttu-id="5ca06-104">Cette énumération est utilisée par la méthode [ICLRMetaHostPolicy :: GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5ca06-104">This enumeration is used by the [ICLRMetaHostPolicy::GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ca06-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5ca06-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="5ca06-106">Membres</span><span class="sxs-lookup"><span data-stu-id="5ca06-106">Members</span></span>  
  
|<span data-ttu-id="5ca06-107">Membre</span><span class="sxs-lookup"><span data-stu-id="5ca06-107">Member</span></span>|<span data-ttu-id="5ca06-108">Description</span><span class="sxs-lookup"><span data-stu-id="5ca06-108">Description</span></span>|  
|------------|-----------------|  
|`METAHOST_POLICY_HIGHCOMPAT`|<span data-ttu-id="5ca06-109">Définit la stratégie de haute compatibilité, qui ne tient pas compte des common language runtime (CLR) chargés dans le processus actuel.</span><span class="sxs-lookup"><span data-stu-id="5ca06-109">Defines the high-compatibility policy, which does not consider any common language runtime (CLR) that is loaded into the current process.</span></span> <span data-ttu-id="5ca06-110">Au lieu de cela, il considère uniquement les CLR installés et les préférences du composant, telles qu’elles sont dérivées du fichier d’assembly lui-même, de la version intégrée déclarée ou du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="5ca06-110">Instead, it considers only the installed CLRs and the preferences of the component, as derived from the assembly file itself, the declared built-against version, or the configuration file.</span></span>|  
|`METAHOST_POLICY_APPLY_UPGRADE_POLICY`|<span data-ttu-id="5ca06-111">Applique la stratégie de mise à niveau au résultat de liaison de version lorsqu’une correspondance exacte est introuvable, en fonction du contenu de HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft \\ . NETFramework\Policy\Upgrades.</span><span class="sxs-lookup"><span data-stu-id="5ca06-111">Applies upgrade policy to the version bind result when an exact match is not found, based on the contents of HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\Policy\Upgrades.</span></span> <span data-ttu-id="5ca06-112">Cela a le même effet que [RUNTIME_INFO_UPGRADE_VERSION](runtime-info-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="5ca06-112">This has the same effect as [RUNTIME_INFO_UPGRADE_VERSION](runtime-info-flags-enumeration.md).</span></span>|  
|`METAHOST_POLICY_EMULATE_EXE_LAUNCH`|<span data-ttu-id="5ca06-113">Les résultats de liaison sont retournés comme si l’image fournie à l’appel avait été lancée dans un nouveau processus.</span><span class="sxs-lookup"><span data-stu-id="5ca06-113">Binding results are returned as if the image provided to the call were launched in a new process.</span></span> <span data-ttu-id="5ca06-114">Actuellement, `GetRequestedRuntime` ignore l’ensemble des runtimes et des liaisons chargeable par rapport au jeu de runtimes installés.</span><span class="sxs-lookup"><span data-stu-id="5ca06-114">Currently, `GetRequestedRuntime` ignores the set of loadable runtimes and binds against the set of installed runtimes.</span></span> <span data-ttu-id="5ca06-115">Cet indicateur permet à un hôte de déterminer à quel Runtime est lié un EXE lorsqu’il est lancé.</span><span class="sxs-lookup"><span data-stu-id="5ca06-115">This flag allows a host to determine which runtime an EXE will bind to when it is launched.</span></span>|  
|`METAHOST_POLICY_SHOW_ERROR_DIALOG`|<span data-ttu-id="5ca06-116">Une boîte de dialogue d’erreur s’affiche si `GetRequestedRuntime` ne parvient pas à trouver un Runtime compatible avec les paramètres d’entrée.</span><span class="sxs-lookup"><span data-stu-id="5ca06-116">An error dialog box is displayed if `GetRequestedRuntime` is unable to find a runtime that is compatible with the input parameters.</span></span> <span data-ttu-id="5ca06-117">À partir de la .NET Framework 4,5, cette boîte de dialogue d’erreur peut prendre la forme d’une boîte de dialogue de fonctionnalité Windows qui vous demande si l’utilisateur souhaite activer la fonctionnalité appropriée.</span><span class="sxs-lookup"><span data-stu-id="5ca06-117">Beginning with the .NET Framework 4.5, this error dialog box can take the form of a Windows feature dialog box that asks whether the user would like to enable the appropriate feature.</span></span>|  
|`METAHOST_POLICY_USE_PROCESS_IMAGE_PATH`|<span data-ttu-id="5ca06-118">`GetRequestedRuntime`utilise l’image de processus (et tout fichier de configuration correspondant) comme entrée supplémentaire dans le processus de liaison.</span><span class="sxs-lookup"><span data-stu-id="5ca06-118">`GetRequestedRuntime` uses the process image (and any corresponding configuration file) as additional input to the binding process.</span></span> <span data-ttu-id="5ca06-119">Par défaut, `GetRequestedRuntime` ne revient pas au chemin d’accès de l’image de processus (en général, le fichier exe qui a été utilisé pour lancer le processus) lors de la détermination du runtime à lier.</span><span class="sxs-lookup"><span data-stu-id="5ca06-119">By default, `GetRequestedRuntime` does not fall back to the process image path (typically, the EXE that was used to launch the process) when determining the runtime to bind to.</span></span>|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|<span data-ttu-id="5ca06-120">`GetRequestedRuntime`doit vérifier si la référence (SKU) appropriée est installée quand aucune information n’est disponible dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="5ca06-120">`GetRequestedRuntime` must check whether the appropriate SKU is installed when no information is available in the configuration file.</span></span> <span data-ttu-id="5ca06-121">Cela permet aux applications qui n’ont pas de fichiers de configuration d’échouer correctement sur des références plus petites que l’installation par défaut de la .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5ca06-121">This allows applications that do not have configuration files to fail gracefully on smaller SKUs than the default installation of the .NET Framework.</span></span> <span data-ttu-id="5ca06-122">Par défaut, `GetRequestedRuntime` ne vérifie pas si la référence SKU appropriée est installée, sauf si l’attribut sku est spécifié dans l’élément fichier de configuration `<supportedRuntime />` .</span><span class="sxs-lookup"><span data-stu-id="5ca06-122">By default, `GetRequestedRuntime` does not check whether the appropriate SKU is installed unless the SKU attribute is specified in the configuration file `<supportedRuntime />` element.</span></span>|  
|`METAHOST_POLICY_IGNORE_ERROR_MODE`|<span data-ttu-id="5ca06-123">`GetRequestedRuntime`doit ignorer SEM_FAILCRITICALERRORS (qui est défini en appelant la fonction [SetErrorMode](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode) ) et afficher la boîte de dialogue d’erreur.</span><span class="sxs-lookup"><span data-stu-id="5ca06-123">`GetRequestedRuntime` should ignore SEM_FAILCRITICALERRORS (which is set by calling the [SetErrorMode](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode) function), and show the error dialog box.</span></span> <span data-ttu-id="5ca06-124">Par défaut, SEM_FAILCRITICALERRORS supprime la boîte de dialogue d’erreur.</span><span class="sxs-lookup"><span data-stu-id="5ca06-124">By default, SEM_FAILCRITICALERRORS suppresses the error dialog box.</span></span> <span data-ttu-id="5ca06-125">Elle a peut-être été héritée d’un autre processus et l’erreur silencieuse peut ne pas être souhaitable dans votre scénario.</span><span class="sxs-lookup"><span data-stu-id="5ca06-125">It may have been inherited from another process, and the silent error may be undesirable in your scenario.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ca06-126">Notes</span><span class="sxs-lookup"><span data-stu-id="5ca06-126">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ca06-127">Spécifications</span><span class="sxs-lookup"><span data-stu-id="5ca06-127">Requirements</span></span>  
 <span data-ttu-id="5ca06-128">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ca06-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ca06-129">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="5ca06-129">**Header:** Metahost.h</span></span>  
  
 <span data-ttu-id="5ca06-130">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5ca06-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5ca06-131">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ca06-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ca06-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5ca06-132">See also</span></span>

- [<span data-ttu-id="5ca06-133">Énumérations d'hébergement</span><span class="sxs-lookup"><span data-stu-id="5ca06-133">Hosting Enumerations</span></span>](hosting-enumerations.md)
- [<span data-ttu-id="5ca06-134">GetRequestedRuntime, méthode</span><span class="sxs-lookup"><span data-stu-id="5ca06-134">GetRequestedRuntime Method</span></span>](iclrmetahostpolicy-getrequestedruntime-method.md)
