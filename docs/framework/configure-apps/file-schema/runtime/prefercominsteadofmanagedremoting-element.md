---
title: Élément <PreferComInsteadOfManagedRemoting>
ms.date: 03/30/2017
helpviewer_keywords:
- <PreferComInsteadOfManagedRemoting> element
- PreferComInsteadOfManagedRemoting element
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e32e4b490f0824cf97a1ae5910d7c74801c7b439
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592689"
---
# <a name="prefercominsteadofmanagedremoting-element"></a><span data-ttu-id="8ea2c-102">\<PreferComInsteadOfManagedRemoting> Element</span><span class="sxs-lookup"><span data-stu-id="8ea2c-102">\<PreferComInsteadOfManagedRemoting> Element</span></span>
<span data-ttu-id="8ea2c-103">Spécifie si le runtime utilisera COM interop au lieu de la communication à distance pour tous les appels entre les limites du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="8ea2c-103">Specifies whether the runtime will use COM interop instead of remoting for all calls across application domain boundaries.</span></span>  
  
 <span data-ttu-id="8ea2c-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="8ea2c-104">\<configuration></span></span>  
<span data-ttu-id="8ea2c-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="8ea2c-105">\<runtime></span></span>  
<span data-ttu-id="8ea2c-106">\<PreferComInsteadOfManagedRemoting></span><span class="sxs-lookup"><span data-stu-id="8ea2c-106">\<PreferComInsteadOfManagedRemoting></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ea2c-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ea2c-107">Syntax</span></span>  
  
```xml  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8ea2c-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="8ea2c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="8ea2c-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="8ea2c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8ea2c-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="8ea2c-110">Attributes</span></span>  
  
|<span data-ttu-id="8ea2c-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="8ea2c-111">Attribute</span></span>|<span data-ttu-id="8ea2c-112">Description</span><span class="sxs-lookup"><span data-stu-id="8ea2c-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="8ea2c-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="8ea2c-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="8ea2c-114">Indique si le runtime utilisera COM interop au lieu de la communication à distance au-delà des limites du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="8ea2c-114">Indicates whether the runtime will use COM interop instead of remoting across application domain boundaries.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="8ea2c-115">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="8ea2c-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="8ea2c-116">Value</span><span class="sxs-lookup"><span data-stu-id="8ea2c-116">Value</span></span>|<span data-ttu-id="8ea2c-117">Description</span><span class="sxs-lookup"><span data-stu-id="8ea2c-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="8ea2c-118">Le runtime utilisera la communication à distance entre les limites du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="8ea2c-118">The runtime will use remoting across application domain boundaries.</span></span> <span data-ttu-id="8ea2c-119">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="8ea2c-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="8ea2c-120">Le runtime utilisera COM interop dans les limites du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="8ea2c-120">The runtime will use COM interop across application domain boundaries.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8ea2c-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8ea2c-121">Child Elements</span></span>  
 <span data-ttu-id="8ea2c-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="8ea2c-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8ea2c-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="8ea2c-123">Parent Elements</span></span>  
  
|<span data-ttu-id="8ea2c-124">Élément</span><span class="sxs-lookup"><span data-stu-id="8ea2c-124">Element</span></span>|<span data-ttu-id="8ea2c-125">Description</span><span class="sxs-lookup"><span data-stu-id="8ea2c-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="8ea2c-126">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8ea2c-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="8ea2c-127">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="8ea2c-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ea2c-128">Notes</span><span class="sxs-lookup"><span data-stu-id="8ea2c-128">Remarks</span></span>  
 <span data-ttu-id="8ea2c-129">Lorsque vous définissez la `enabled` attribut `true`, le runtime se comporte comme suit :</span><span class="sxs-lookup"><span data-stu-id="8ea2c-129">When you set the `enabled` attribute to `true`, the runtime behaves as follows:</span></span>  
  
- <span data-ttu-id="8ea2c-130">Le runtime n’appelle pas [IUnknown::QueryInterface](https://go.microsoft.com/fwlink/?LinkID=144867) pour un [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) interface quand un [IUnknown](https://go.microsoft.com/fwlink/?LinkId=148003) accède au domaine via une interface COM.</span><span class="sxs-lookup"><span data-stu-id="8ea2c-130">The runtime does not call [IUnknown::QueryInterface](https://go.microsoft.com/fwlink/?LinkID=144867) for an [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) interface when an [IUnknown](https://go.microsoft.com/fwlink/?LinkId=148003) interface enters the domain through a COM interface.</span></span> <span data-ttu-id="8ea2c-131">Au lieu de cela, il construit un [Runtime Callable Wrapper](../../../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) autour de l’objet.</span><span class="sxs-lookup"><span data-stu-id="8ea2c-131">Instead, it constructs a [Runtime Callable Wrapper](../../../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) around the object.</span></span>  
  
- <span data-ttu-id="8ea2c-132">Le runtime retourne E_NOINTERFACE lorsqu’il reçoit un `QueryInterface` appeler pour un [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) interface pour toute [Wrapper CCW](../../../../../docs/framework/interop/com-callable-wrapper.md) (wrapper CCW) qui a été créé dans ce domaine.</span><span class="sxs-lookup"><span data-stu-id="8ea2c-132">The runtime returns E_NOINTERFACE when it receives a `QueryInterface` call for an [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) interface for any [COM Callable Wrapper](../../../../../docs/framework/interop/com-callable-wrapper.md) (CCW) that has been created in this domain.</span></span>  
  
 <span data-ttu-id="8ea2c-133">Ces deux comportements garantissent que tous les appels via COM des interfaces entre les objets gérés sur l’utilisation des limites de domaine l’application COM et COM interop au lieu de la communication à distance.</span><span class="sxs-lookup"><span data-stu-id="8ea2c-133">These two behaviors ensure that all calls over COM interfaces between managed objects across application domain boundaries use COM and COM interop instead of remoting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ea2c-134">Exemple</span><span class="sxs-lookup"><span data-stu-id="8ea2c-134">Example</span></span>  
 <span data-ttu-id="8ea2c-135">L’exemple suivant montre comment spécifier que le runtime doit utiliser COM interop au-delà des limites d’isolation :</span><span class="sxs-lookup"><span data-stu-id="8ea2c-135">The following example shows how to specify that the runtime should use COM interop across isolation boundaries:</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8ea2c-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ea2c-136">See also</span></span>

- [<span data-ttu-id="8ea2c-137">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="8ea2c-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="8ea2c-138">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="8ea2c-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
