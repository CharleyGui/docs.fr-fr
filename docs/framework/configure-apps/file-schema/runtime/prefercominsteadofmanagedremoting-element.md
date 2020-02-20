---
title: Élément <PreferComInsteadOfManagedRemoting>
ms.date: 03/30/2017
helpviewer_keywords:
- <PreferComInsteadOfManagedRemoting> element
- PreferComInsteadOfManagedRemoting element
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
ms.openlocfilehash: 1376df4efd56734f2b8da9bd76033afcce8a285b
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452251"
---
# <a name="prefercominsteadofmanagedremoting-element"></a><span data-ttu-id="2cfdc-102">\<élément PreferComInsteadOfManagedRemoting ></span><span class="sxs-lookup"><span data-stu-id="2cfdc-102">\<PreferComInsteadOfManagedRemoting> Element</span></span>
<span data-ttu-id="2cfdc-103">Spécifie si le runtime utilisera COM Interop au lieu de la communication à distance pour tous les appels au-delà des limites du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-103">Specifies whether the runtime will use COM interop instead of remoting for all calls across application domain boundaries.</span></span>  
  
<span data-ttu-id="2cfdc-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2cfdc-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2cfdc-105">&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="2cfdc-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="2cfdc-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<PreferComInsteadOfManagedRemoting** ></span><span class="sxs-lookup"><span data-stu-id="2cfdc-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<PreferComInsteadOfManagedRemoting>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cfdc-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2cfdc-107">Syntax</span></span>  
  
```xml  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2cfdc-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="2cfdc-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2cfdc-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2cfdc-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="2cfdc-110">Attributes</span></span>  
  
|<span data-ttu-id="2cfdc-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="2cfdc-111">Attribute</span></span>|<span data-ttu-id="2cfdc-112">Description</span><span class="sxs-lookup"><span data-stu-id="2cfdc-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="2cfdc-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="2cfdc-114">Indique si le runtime utilisera COM Interop au lieu de la communication à distance au-delà des limites du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-114">Indicates whether the runtime will use COM interop instead of remoting across application domain boundaries.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="2cfdc-115">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="2cfdc-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="2cfdc-116">Valeur</span><span class="sxs-lookup"><span data-stu-id="2cfdc-116">Value</span></span>|<span data-ttu-id="2cfdc-117">Description</span><span class="sxs-lookup"><span data-stu-id="2cfdc-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="2cfdc-118">Le runtime utilise la communication à distance au-delà des limites du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-118">The runtime will use remoting across application domain boundaries.</span></span> <span data-ttu-id="2cfdc-119">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="2cfdc-120">Le runtime utilisera COM Interop à travers les limites du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-120">The runtime will use COM interop across application domain boundaries.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2cfdc-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2cfdc-121">Child Elements</span></span>  
 <span data-ttu-id="2cfdc-122">None.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2cfdc-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2cfdc-123">Parent Elements</span></span>  
  
|<span data-ttu-id="2cfdc-124">Élément</span><span class="sxs-lookup"><span data-stu-id="2cfdc-124">Element</span></span>|<span data-ttu-id="2cfdc-125">Description</span><span class="sxs-lookup"><span data-stu-id="2cfdc-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="2cfdc-126">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="2cfdc-127">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2cfdc-128">Notes</span><span class="sxs-lookup"><span data-stu-id="2cfdc-128">Remarks</span></span>  
 <span data-ttu-id="2cfdc-129">Lorsque vous affectez à l’attribut `enabled` la valeur `true`, le runtime se comporte comme suit :</span><span class="sxs-lookup"><span data-stu-id="2cfdc-129">When you set the `enabled` attribute to `true`, the runtime behaves as follows:</span></span>  
  
- <span data-ttu-id="2cfdc-130">Le runtime n’appelle pas [IUnknown :: QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) pour une interface [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) lorsqu’une interface [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) entre dans le domaine via une interface com.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-130">The runtime does not call [IUnknown::QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) for an [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) interface when an [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) interface enters the domain through a COM interface.</span></span> <span data-ttu-id="2cfdc-131">Au lieu de cela, il construit un wrapper RCW ( [Runtime Callable Wrapper](../../../../standard/native-interop/runtime-callable-wrapper.md) ) autour de l’objet.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-131">Instead, it constructs a [Runtime Callable Wrapper](../../../../standard/native-interop/runtime-callable-wrapper.md) (RCW) around the object.</span></span>  
  
- <span data-ttu-id="2cfdc-132">Le runtime retourne E_NOINTERFACE lorsqu’il reçoit un appel de `QueryInterface` pour une interface [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) pour tout wrapper CCW ( [COM Callable Wrapper](../../../../standard/native-interop/com-callable-wrapper.md) ) qui a été créé dans ce domaine.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-132">The runtime returns E_NOINTERFACE when it receives a `QueryInterface` call for an [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) interface for any [COM Callable Wrapper](../../../../standard/native-interop/com-callable-wrapper.md) (CCW) that has been created in this domain.</span></span>  
  
 <span data-ttu-id="2cfdc-133">Ces deux comportements garantissent que tous les appels sur les interfaces COM entre les objets gérés au-delà des limites du domaine d’application utilisent COM et COM Interop au lieu de la communication à distance.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-133">These two behaviors ensure that all calls over COM interfaces between managed objects across application domain boundaries use COM and COM interop instead of remoting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2cfdc-134">Exemple</span><span class="sxs-lookup"><span data-stu-id="2cfdc-134">Example</span></span>  
 <span data-ttu-id="2cfdc-135">L’exemple suivant montre comment spécifier que le runtime doit utiliser COM Interop à travers les limites d’isolation :</span><span class="sxs-lookup"><span data-stu-id="2cfdc-135">The following example shows how to specify that the runtime should use COM interop across isolation boundaries:</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2cfdc-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2cfdc-136">See also</span></span>

- [<span data-ttu-id="2cfdc-137">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="2cfdc-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="2cfdc-138">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="2cfdc-138">Configuration File Schema</span></span>](../index.md)
