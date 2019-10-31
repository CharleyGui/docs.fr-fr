---
title: Élément <PreferComInsteadOfManagedRemoting>
ms.date: 03/30/2017
helpviewer_keywords:
- <PreferComInsteadOfManagedRemoting> element
- PreferComInsteadOfManagedRemoting element
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
ms.openlocfilehash: 47c568a8d6e89a195414552b3db5953ee61d1e55
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116014"
---
# <a name="prefercominsteadofmanagedremoting-element"></a><span data-ttu-id="30ddf-102">\<élément PreferComInsteadOfManagedRemoting ></span><span class="sxs-lookup"><span data-stu-id="30ddf-102">\<PreferComInsteadOfManagedRemoting> Element</span></span>
<span data-ttu-id="30ddf-103">Spécifie si le runtime utilisera COM Interop au lieu de la communication à distance pour tous les appels au-delà des limites du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="30ddf-103">Specifies whether the runtime will use COM interop instead of remoting for all calls across application domain boundaries.</span></span>  
  
<span data-ttu-id="30ddf-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="30ddf-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="30ddf-105">&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="30ddf-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="30ddf-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<PreferComInsteadOfManagedRemoting** ></span><span class="sxs-lookup"><span data-stu-id="30ddf-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<PreferComInsteadOfManagedRemoting>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30ddf-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="30ddf-107">Syntax</span></span>  
  
```xml  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="30ddf-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="30ddf-108">Attributes and Elements</span></span>  
 <span data-ttu-id="30ddf-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="30ddf-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="30ddf-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="30ddf-110">Attributes</span></span>  
  
|<span data-ttu-id="30ddf-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="30ddf-111">Attribute</span></span>|<span data-ttu-id="30ddf-112">Description</span><span class="sxs-lookup"><span data-stu-id="30ddf-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="30ddf-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="30ddf-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="30ddf-114">Indique si le runtime utilisera COM Interop au lieu de la communication à distance au-delà des limites du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="30ddf-114">Indicates whether the runtime will use COM interop instead of remoting across application domain boundaries.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="30ddf-115">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="30ddf-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="30ddf-116">valeur</span><span class="sxs-lookup"><span data-stu-id="30ddf-116">Value</span></span>|<span data-ttu-id="30ddf-117">Description</span><span class="sxs-lookup"><span data-stu-id="30ddf-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="30ddf-118">Le runtime utilise la communication à distance au-delà des limites du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="30ddf-118">The runtime will use remoting across application domain boundaries.</span></span> <span data-ttu-id="30ddf-119">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="30ddf-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="30ddf-120">Le runtime utilisera COM Interop à travers les limites du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="30ddf-120">The runtime will use COM interop across application domain boundaries.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="30ddf-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="30ddf-121">Child Elements</span></span>  
 <span data-ttu-id="30ddf-122">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="30ddf-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="30ddf-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="30ddf-123">Parent Elements</span></span>  
  
|<span data-ttu-id="30ddf-124">Élément</span><span class="sxs-lookup"><span data-stu-id="30ddf-124">Element</span></span>|<span data-ttu-id="30ddf-125">Description</span><span class="sxs-lookup"><span data-stu-id="30ddf-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="30ddf-126">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="30ddf-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="30ddf-127">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="30ddf-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30ddf-128">Notes</span><span class="sxs-lookup"><span data-stu-id="30ddf-128">Remarks</span></span>  
 <span data-ttu-id="30ddf-129">Lorsque vous affectez à l’attribut `enabled` la valeur `true`, le runtime se comporte comme suit :</span><span class="sxs-lookup"><span data-stu-id="30ddf-129">When you set the `enabled` attribute to `true`, the runtime behaves as follows:</span></span>  
  
- <span data-ttu-id="30ddf-130">Le runtime n’appelle pas [IUnknown :: QueryInterface](https://go.microsoft.com/fwlink/?LinkID=144867) pour une interface [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) lorsqu’une interface [IUnknown](https://go.microsoft.com/fwlink/?LinkId=148003) entre dans le domaine via une interface com.</span><span class="sxs-lookup"><span data-stu-id="30ddf-130">The runtime does not call [IUnknown::QueryInterface](https://go.microsoft.com/fwlink/?LinkID=144867) for an [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) interface when an [IUnknown](https://go.microsoft.com/fwlink/?LinkId=148003) interface enters the domain through a COM interface.</span></span> <span data-ttu-id="30ddf-131">Au lieu de cela, il construit un wrapper RCW ( [Runtime Callable Wrapper](../../../../standard/native-interop/runtime-callable-wrapper.md) ) autour de l’objet.</span><span class="sxs-lookup"><span data-stu-id="30ddf-131">Instead, it constructs a [Runtime Callable Wrapper](../../../../standard/native-interop/runtime-callable-wrapper.md) (RCW) around the object.</span></span>  
  
- <span data-ttu-id="30ddf-132">Le runtime retourne E_NOINTERFACE lorsqu’il reçoit un appel de `QueryInterface` pour une interface [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) pour tout wrapper CCW ( [COM Callable Wrapper](../../../../standard/native-interop/com-callable-wrapper.md) ) qui a été créé dans ce domaine.</span><span class="sxs-lookup"><span data-stu-id="30ddf-132">The runtime returns E_NOINTERFACE when it receives a `QueryInterface` call for an [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) interface for any [COM Callable Wrapper](../../../../standard/native-interop/com-callable-wrapper.md) (CCW) that has been created in this domain.</span></span>  
  
 <span data-ttu-id="30ddf-133">Ces deux comportements garantissent que tous les appels sur les interfaces COM entre les objets gérés au-delà des limites du domaine d’application utilisent COM et COM Interop au lieu de la communication à distance.</span><span class="sxs-lookup"><span data-stu-id="30ddf-133">These two behaviors ensure that all calls over COM interfaces between managed objects across application domain boundaries use COM and COM interop instead of remoting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30ddf-134">Exemple</span><span class="sxs-lookup"><span data-stu-id="30ddf-134">Example</span></span>  
 <span data-ttu-id="30ddf-135">L’exemple suivant montre comment spécifier que le runtime doit utiliser COM Interop à travers les limites d’isolation :</span><span class="sxs-lookup"><span data-stu-id="30ddf-135">The following example shows how to specify that the runtime should use COM interop across isolation boundaries:</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="30ddf-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="30ddf-136">See also</span></span>

- [<span data-ttu-id="30ddf-137">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="30ddf-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="30ddf-138">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="30ddf-138">Configuration File Schema</span></span>](../index.md)
