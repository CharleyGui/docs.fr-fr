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
ms.openlocfilehash: f717f57fe8670b126ed1468713a2114aaa772762
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198988"
---
# <a name="disablecommitthreadstack-element"></a><span data-ttu-id="0682c-102">Élément \<disableCommitThreadStack></span><span class="sxs-lookup"><span data-stu-id="0682c-102">\<disableCommitThreadStack> Element</span></span>

<span data-ttu-id="0682c-103">Spécifie si la pile des threads complète est validée quand un thread est démarré.</span><span class="sxs-lookup"><span data-stu-id="0682c-103">Specifies whether the full thread stack is committed when a thread is started.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<disableCommitThreadStack>**  
  
## <a name="syntax"></a><span data-ttu-id="0682c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0682c-104">Syntax</span></span>  
  
```xml  
<disableCommitThreadStack enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0682c-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0682c-105">Attributes and Elements</span></span>  

 <span data-ttu-id="0682c-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="0682c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0682c-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="0682c-107">Attributes</span></span>  
  
|<span data-ttu-id="0682c-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="0682c-108">Attribute</span></span>|<span data-ttu-id="0682c-109">Description</span><span class="sxs-lookup"><span data-stu-id="0682c-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0682c-110">enabled</span><span class="sxs-lookup"><span data-stu-id="0682c-110">enabled</span></span>|<span data-ttu-id="0682c-111">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="0682c-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="0682c-112">Spécifie si la validation de la pile des threads complète lors du démarrage de thread (comportement par défaut) est désactivée.</span><span class="sxs-lookup"><span data-stu-id="0682c-112">Specifies whether committing the full thread stack on thread startup (the default behavior) is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="0682c-113">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="0682c-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="0682c-114">Valeur</span><span class="sxs-lookup"><span data-stu-id="0682c-114">Value</span></span>|<span data-ttu-id="0682c-115">Description</span><span class="sxs-lookup"><span data-stu-id="0682c-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0682c-116">0</span><span class="sxs-lookup"><span data-stu-id="0682c-116">0</span></span>|<span data-ttu-id="0682c-117">Ne pas désactiver le comportement par défaut du Common Language Runtime, qui consiste à valider la pile des threads complète quand un thread est démarré.</span><span class="sxs-lookup"><span data-stu-id="0682c-117">Do not disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
|<span data-ttu-id="0682c-118">1</span><span class="sxs-lookup"><span data-stu-id="0682c-118">1</span></span>|<span data-ttu-id="0682c-119">Désactiver le comportement par défaut du Common Language Runtime, qui consiste à valider la pile des threads complète quand un thread est démarré.</span><span class="sxs-lookup"><span data-stu-id="0682c-119">Disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0682c-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0682c-120">Child Elements</span></span>  

 <span data-ttu-id="0682c-121">Aucun.</span><span class="sxs-lookup"><span data-stu-id="0682c-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0682c-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0682c-122">Parent Elements</span></span>  
  
|<span data-ttu-id="0682c-123">Élément</span><span class="sxs-lookup"><span data-stu-id="0682c-123">Element</span></span>|<span data-ttu-id="0682c-124">Description</span><span class="sxs-lookup"><span data-stu-id="0682c-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0682c-125">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0682c-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="0682c-126">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="0682c-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0682c-127">Notes</span><span class="sxs-lookup"><span data-stu-id="0682c-127">Remarks</span></span>  

 <span data-ttu-id="0682c-128">Le comportement par défaut du Common Language Runtime consiste à valider la pile des threads complète quand un thread est démarré.</span><span class="sxs-lookup"><span data-stu-id="0682c-128">The default behavior of the common language runtime is to commit the full thread stack when a thread is started.</span></span> <span data-ttu-id="0682c-129">Si un grand nombre de threads doivent être créés sur un serveur disposant d’une mémoire limitée, et que la plupart de ces threads utilisent très peu d’espace de pile, les performances du serveur peuvent être améliorées si le Common Language Runtime ne valide pas la pile des threads complète immédiatement quand un thread est démarré.</span><span class="sxs-lookup"><span data-stu-id="0682c-129">If a large number of threads must be created on a server that has limited memory, and most of those threads will use very little stack space, the server might perform better if the common language runtime does not commit the full thread stack immediately when a thread is started.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0682c-130">Les hôtes non managés peuvent utiliser l’indicateur de démarrage `STARTUP_DISABLE_COMMITTHREADSTACK` dans l’énumération [STARTUP_FLAGS](../../../unmanaged-api/hosting/startup-flags-enumeration.md) pour obtenir le même résultat.</span><span class="sxs-lookup"><span data-stu-id="0682c-130">Unmanaged hosts can use the `STARTUP_DISABLE_COMMITTHREADSTACK` startup flag in the [STARTUP_FLAGS](../../../unmanaged-api/hosting/startup-flags-enumeration.md) enumeration to accomplish the same result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0682c-131">Exemple</span><span class="sxs-lookup"><span data-stu-id="0682c-131">Example</span></span>  

 <span data-ttu-id="0682c-132">L’exemple suivant montre comment désactiver le comportement par défaut du Common Language Runtime, qui consiste à valider la pile des threads complète lors du démarrage d’un thread.</span><span class="sxs-lookup"><span data-stu-id="0682c-132">The following example shows how to disable the default behavior of the common language runtime, which is to commit the full thread stack on thread startup.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCommitThreadStack enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0682c-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0682c-133">See also</span></span>

- [<span data-ttu-id="0682c-134">Schéma des paramètres d'exécution</span><span class="sxs-lookup"><span data-stu-id="0682c-134">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="0682c-135">Schéma du fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="0682c-135">Configuration File Schema</span></span>](../index.md)
