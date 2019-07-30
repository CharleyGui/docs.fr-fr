---
title: Élément <PreferComInsteadOfManagedRemoting>
ms.date: 03/30/2017
helpviewer_keywords:
- <PreferComInsteadOfManagedRemoting> element
- PreferComInsteadOfManagedRemoting element
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c7a558af17493c955b4f148d0abf7f42c9dd6f8
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629437"
---
# <a name="prefercominsteadofmanagedremoting-element"></a><span data-ttu-id="65dd1-102">\<PreferComInsteadOfManagedRemoting >, élément</span><span class="sxs-lookup"><span data-stu-id="65dd1-102">\<PreferComInsteadOfManagedRemoting> Element</span></span>
<span data-ttu-id="65dd1-103">Spécifie si le runtime utilisera COM Interop au lieu de la communication à distance pour tous les appels au-delà des limites du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="65dd1-103">Specifies whether the runtime will use COM interop instead of remoting for all calls across application domain boundaries.</span></span>  
  
 <span data-ttu-id="65dd1-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="65dd1-104">\<configuration></span></span>  
<span data-ttu-id="65dd1-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="65dd1-105">\<runtime></span></span>  
<span data-ttu-id="65dd1-106">\<PreferComInsteadOfManagedRemoting></span><span class="sxs-lookup"><span data-stu-id="65dd1-106">\<PreferComInsteadOfManagedRemoting></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65dd1-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="65dd1-107">Syntax</span></span>  
  
```xml  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="65dd1-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="65dd1-108">Attributes and Elements</span></span>  
 <span data-ttu-id="65dd1-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="65dd1-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="65dd1-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="65dd1-110">Attributes</span></span>  
  
|<span data-ttu-id="65dd1-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="65dd1-111">Attribute</span></span>|<span data-ttu-id="65dd1-112">Description</span><span class="sxs-lookup"><span data-stu-id="65dd1-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="65dd1-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="65dd1-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="65dd1-114">Indique si le runtime utilisera COM Interop au lieu de la communication à distance au-delà des limites du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="65dd1-114">Indicates whether the runtime will use COM interop instead of remoting across application domain boundaries.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="65dd1-115">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="65dd1-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="65dd1-116">`Value`</span><span class="sxs-lookup"><span data-stu-id="65dd1-116">Value</span></span>|<span data-ttu-id="65dd1-117">Description</span><span class="sxs-lookup"><span data-stu-id="65dd1-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="65dd1-118">Le runtime utilise la communication à distance au-delà des limites du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="65dd1-118">The runtime will use remoting across application domain boundaries.</span></span> <span data-ttu-id="65dd1-119">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="65dd1-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="65dd1-120">Le runtime utilisera COM Interop à travers les limites du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="65dd1-120">The runtime will use COM interop across application domain boundaries.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="65dd1-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="65dd1-121">Child Elements</span></span>  
 <span data-ttu-id="65dd1-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="65dd1-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="65dd1-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="65dd1-123">Parent Elements</span></span>  
  
|<span data-ttu-id="65dd1-124">Élément</span><span class="sxs-lookup"><span data-stu-id="65dd1-124">Element</span></span>|<span data-ttu-id="65dd1-125">Description</span><span class="sxs-lookup"><span data-stu-id="65dd1-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="65dd1-126">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="65dd1-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="65dd1-127">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="65dd1-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="65dd1-128">Notes</span><span class="sxs-lookup"><span data-stu-id="65dd1-128">Remarks</span></span>  
 <span data-ttu-id="65dd1-129">Lorsque vous affectez `enabled` à `true`l’attribut la valeur, le runtime se comporte comme suit:</span><span class="sxs-lookup"><span data-stu-id="65dd1-129">When you set the `enabled` attribute to `true`, the runtime behaves as follows:</span></span>  
  
- <span data-ttu-id="65dd1-130">Le runtime n’appelle pas [IUnknown:: QueryInterface](https://go.microsoft.com/fwlink/?LinkID=144867) pour une interface [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) lorsqu’une interface [IUnknown](https://go.microsoft.com/fwlink/?LinkId=148003) entre dans le domaine via une interface com.</span><span class="sxs-lookup"><span data-stu-id="65dd1-130">The runtime does not call [IUnknown::QueryInterface](https://go.microsoft.com/fwlink/?LinkID=144867) for an [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) interface when an [IUnknown](https://go.microsoft.com/fwlink/?LinkId=148003) interface enters the domain through a COM interface.</span></span> <span data-ttu-id="65dd1-131">Au lieu de cela, il construit un wrapper RCW ( [Runtime Callable Wrapper](../../../../../docs/standard/native-interop/runtime-callable-wrapper.md) ) autour de l’objet.</span><span class="sxs-lookup"><span data-stu-id="65dd1-131">Instead, it constructs a [Runtime Callable Wrapper](../../../../../docs/standard/native-interop/runtime-callable-wrapper.md) (RCW) around the object.</span></span>  
  
- <span data-ttu-id="65dd1-132">Le runtime retourne E_NOINTERFACE lorsqu’il reçoit un `QueryInterface` appel pour une interface [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) pour tout [wrapper CCW (COM Callable Wrapper](../../../../../docs/standard/native-interop/com-callable-wrapper.md) ) qui a été créé dans ce domaine.</span><span class="sxs-lookup"><span data-stu-id="65dd1-132">The runtime returns E_NOINTERFACE when it receives a `QueryInterface` call for an [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) interface for any [COM Callable Wrapper](../../../../../docs/standard/native-interop/com-callable-wrapper.md) (CCW) that has been created in this domain.</span></span>  
  
 <span data-ttu-id="65dd1-133">Ces deux comportements garantissent que tous les appels sur les interfaces COM entre les objets gérés au-delà des limites du domaine d’application utilisent COM et COM Interop au lieu de la communication à distance.</span><span class="sxs-lookup"><span data-stu-id="65dd1-133">These two behaviors ensure that all calls over COM interfaces between managed objects across application domain boundaries use COM and COM interop instead of remoting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="65dd1-134">Exemple</span><span class="sxs-lookup"><span data-stu-id="65dd1-134">Example</span></span>  
 <span data-ttu-id="65dd1-135">L’exemple suivant montre comment spécifier que le runtime doit utiliser COM Interop à travers les limites d’isolation:</span><span class="sxs-lookup"><span data-stu-id="65dd1-135">The following example shows how to specify that the runtime should use COM interop across isolation boundaries:</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="65dd1-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="65dd1-136">See also</span></span>

- [<span data-ttu-id="65dd1-137">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="65dd1-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="65dd1-138">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="65dd1-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
