---
title: Élément <disableCommitThreadStack>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCommitThreadStack
- http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCommitThreadStack
helpviewer_keywords:
- <disableCommitThreadStack> element
- disableCommitThreadStack element
ms.assetid: 3559d46a-7640-4c72-9a11-7e980768929e
ms.openlocfilehash: 8aefb8a20d6a95c5b8062d0c03dcb28a3557ca3d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73117475"
---
# <a name="disablecommitthreadstack-element"></a><span data-ttu-id="88a5e-102">\<élément disableCommitThreadStack ></span><span class="sxs-lookup"><span data-stu-id="88a5e-102">\<disableCommitThreadStack> Element</span></span>
<span data-ttu-id="88a5e-103">Spécifie si la pile des threads complète est validée quand un thread est démarré.</span><span class="sxs-lookup"><span data-stu-id="88a5e-103">Specifies whether the full thread stack is committed when a thread is started.</span></span>  
  
<span data-ttu-id="88a5e-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="88a5e-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="88a5e-105">&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="88a5e-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="88a5e-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<disableCommitThreadStack** ></span><span class="sxs-lookup"><span data-stu-id="88a5e-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<disableCommitThreadStack>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88a5e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="88a5e-107">Syntax</span></span>  
  
```xml  
<disableCommitThreadStack enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="88a5e-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="88a5e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="88a5e-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="88a5e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="88a5e-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="88a5e-110">Attributes</span></span>  
  
|<span data-ttu-id="88a5e-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="88a5e-111">Attribute</span></span>|<span data-ttu-id="88a5e-112">Description</span><span class="sxs-lookup"><span data-stu-id="88a5e-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="88a5e-113">enabled</span><span class="sxs-lookup"><span data-stu-id="88a5e-113">enabled</span></span>|<span data-ttu-id="88a5e-114">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="88a5e-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="88a5e-115">Spécifie si la validation de la pile des threads complète lors du démarrage de thread (comportement par défaut) est désactivée.</span><span class="sxs-lookup"><span data-stu-id="88a5e-115">Specifies whether committing the full thread stack on thread startup (the default behavior) is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="88a5e-116">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="88a5e-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="88a5e-117">valeur</span><span class="sxs-lookup"><span data-stu-id="88a5e-117">Value</span></span>|<span data-ttu-id="88a5e-118">Description</span><span class="sxs-lookup"><span data-stu-id="88a5e-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="88a5e-119">0</span><span class="sxs-lookup"><span data-stu-id="88a5e-119">0</span></span>|<span data-ttu-id="88a5e-120">Ne pas désactiver le comportement par défaut du Common Language Runtime, qui consiste à valider la pile des threads complète quand un thread est démarré.</span><span class="sxs-lookup"><span data-stu-id="88a5e-120">Do not disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
|<span data-ttu-id="88a5e-121">1</span><span class="sxs-lookup"><span data-stu-id="88a5e-121">1</span></span>|<span data-ttu-id="88a5e-122">Désactiver le comportement par défaut du Common Language Runtime, qui consiste à valider la pile des threads complète quand un thread est démarré.</span><span class="sxs-lookup"><span data-stu-id="88a5e-122">Disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="88a5e-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="88a5e-123">Child Elements</span></span>  
 <span data-ttu-id="88a5e-124">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="88a5e-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="88a5e-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="88a5e-125">Parent Elements</span></span>  
  
|<span data-ttu-id="88a5e-126">Élément</span><span class="sxs-lookup"><span data-stu-id="88a5e-126">Element</span></span>|<span data-ttu-id="88a5e-127">Description</span><span class="sxs-lookup"><span data-stu-id="88a5e-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="88a5e-128">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="88a5e-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="88a5e-129">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="88a5e-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="88a5e-130">Notes</span><span class="sxs-lookup"><span data-stu-id="88a5e-130">Remarks</span></span>  
 <span data-ttu-id="88a5e-131">Le comportement par défaut du Common Language Runtime consiste à valider la pile des threads complète quand un thread est démarré.</span><span class="sxs-lookup"><span data-stu-id="88a5e-131">The default behavior of the common language runtime is to commit the full thread stack when a thread is started.</span></span> <span data-ttu-id="88a5e-132">Si un grand nombre de threads doivent être créés sur un serveur disposant d’une mémoire limitée, et que la plupart de ces threads utilisent très peu d’espace de pile, les performances du serveur peuvent être améliorées si le Common Language Runtime ne valide pas la pile des threads complète immédiatement quand un thread est démarré.</span><span class="sxs-lookup"><span data-stu-id="88a5e-132">If a large number of threads must be created on a server that has limited memory, and most of those threads will use very little stack space, the server might perform better if the common language runtime does not commit the full thread stack immediately when a thread is started.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="88a5e-133">Les hôtes non managés peuvent utiliser l’indicateur de démarrage `STARTUP_DISABLE_COMMITTHREADSTACK` dans l’énumération [STARTUP_FLAGS](../../../unmanaged-api/hosting/startup-flags-enumeration.md) pour obtenir le même résultat.</span><span class="sxs-lookup"><span data-stu-id="88a5e-133">Unmanaged hosts can use the `STARTUP_DISABLE_COMMITTHREADSTACK` startup flag in the [STARTUP_FLAGS](../../../unmanaged-api/hosting/startup-flags-enumeration.md) enumeration to accomplish the same result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88a5e-134">Exemple</span><span class="sxs-lookup"><span data-stu-id="88a5e-134">Example</span></span>  
 <span data-ttu-id="88a5e-135">L’exemple suivant montre comment désactiver le comportement par défaut du Common Language Runtime, qui consiste à valider la pile des threads complète lors du démarrage d’un thread.</span><span class="sxs-lookup"><span data-stu-id="88a5e-135">The following example shows how to disable the default behavior of the common language runtime, which is to commit the full thread stack on thread startup.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCommitThreadStack enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="88a5e-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="88a5e-136">See also</span></span>

- [<span data-ttu-id="88a5e-137">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="88a5e-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="88a5e-138">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="88a5e-138">Configuration File Schema</span></span>](../index.md)
