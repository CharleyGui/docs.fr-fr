---
title: Élément <PreferComInsteadOfManagedRemoting>
ms.date: 03/30/2017
helpviewer_keywords:
- <PreferComInsteadOfManagedRemoting> element
- PreferComInsteadOfManagedRemoting element
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
ms.openlocfilehash: 2fb0d94f91d28f9d9d4f247411d273f786f7b63b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195283"
---
# <a name="prefercominsteadofmanagedremoting-element"></a><span data-ttu-id="6ee46-102">Élément \<PreferComInsteadOfManagedRemoting></span><span class="sxs-lookup"><span data-stu-id="6ee46-102">\<PreferComInsteadOfManagedRemoting> Element</span></span>

<span data-ttu-id="6ee46-103">Spécifie si le runtime utilisera COM Interop au lieu de la communication à distance pour tous les appels au-delà des limites du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="6ee46-103">Specifies whether the runtime will use COM interop instead of remoting for all calls across application domain boundaries.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<PreferComInsteadOfManagedRemoting>**  
  
## <a name="syntax"></a><span data-ttu-id="6ee46-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6ee46-104">Syntax</span></span>  
  
```xml  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6ee46-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="6ee46-105">Attributes and Elements</span></span>  

 <span data-ttu-id="6ee46-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="6ee46-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6ee46-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="6ee46-107">Attributes</span></span>  
  
|<span data-ttu-id="6ee46-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="6ee46-108">Attribute</span></span>|<span data-ttu-id="6ee46-109">Description</span><span class="sxs-lookup"><span data-stu-id="6ee46-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="6ee46-110">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="6ee46-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="6ee46-111">Indique si le runtime utilisera COM Interop au lieu de la communication à distance au-delà des limites du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="6ee46-111">Indicates whether the runtime will use COM interop instead of remoting across application domain boundaries.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="6ee46-112">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="6ee46-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="6ee46-113">Valeur</span><span class="sxs-lookup"><span data-stu-id="6ee46-113">Value</span></span>|<span data-ttu-id="6ee46-114">Description</span><span class="sxs-lookup"><span data-stu-id="6ee46-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="6ee46-115">Le runtime utilise la communication à distance au-delà des limites du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="6ee46-115">The runtime will use remoting across application domain boundaries.</span></span> <span data-ttu-id="6ee46-116">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="6ee46-116">This is the default.</span></span>|  
|`true`|<span data-ttu-id="6ee46-117">Le runtime utilisera COM Interop à travers les limites du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="6ee46-117">The runtime will use COM interop across application domain boundaries.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6ee46-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6ee46-118">Child Elements</span></span>  

 <span data-ttu-id="6ee46-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="6ee46-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6ee46-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6ee46-120">Parent Elements</span></span>  
  
|<span data-ttu-id="6ee46-121">Élément</span><span class="sxs-lookup"><span data-stu-id="6ee46-121">Element</span></span>|<span data-ttu-id="6ee46-122">Description</span><span class="sxs-lookup"><span data-stu-id="6ee46-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6ee46-123">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6ee46-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="6ee46-124">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="6ee46-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ee46-125">Notes</span><span class="sxs-lookup"><span data-stu-id="6ee46-125">Remarks</span></span>  

 <span data-ttu-id="6ee46-126">Lorsque vous affectez `enabled` à l’attribut la valeur `true` , le runtime se comporte comme suit :</span><span class="sxs-lookup"><span data-stu-id="6ee46-126">When you set the `enabled` attribute to `true`, the runtime behaves as follows:</span></span>  
  
- <span data-ttu-id="6ee46-127">Le runtime n’appelle pas [IUnknown :: QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) pour une interface [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) lorsqu’une interface [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) entre dans le domaine via une interface com.</span><span class="sxs-lookup"><span data-stu-id="6ee46-127">The runtime does not call [IUnknown::QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) for an [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) interface when an [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) interface enters the domain through a COM interface.</span></span> <span data-ttu-id="6ee46-128">Au lieu de cela, il construit un wrapper RCW ( [Runtime Callable Wrapper](../../../../standard/native-interop/runtime-callable-wrapper.md) ) autour de l’objet.</span><span class="sxs-lookup"><span data-stu-id="6ee46-128">Instead, it constructs a [Runtime Callable Wrapper](../../../../standard/native-interop/runtime-callable-wrapper.md) (RCW) around the object.</span></span>  
  
- <span data-ttu-id="6ee46-129">Le runtime retourne E_NOINTERFACE lorsqu’il reçoit un `QueryInterface` appel pour une interface [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) pour tout [wrapper CCW (COM Callable Wrapper](../../../../standard/native-interop/com-callable-wrapper.md) ) qui a été créé dans ce domaine.</span><span class="sxs-lookup"><span data-stu-id="6ee46-129">The runtime returns E_NOINTERFACE when it receives a `QueryInterface` call for an [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) interface for any [COM Callable Wrapper](../../../../standard/native-interop/com-callable-wrapper.md) (CCW) that has been created in this domain.</span></span>  
  
 <span data-ttu-id="6ee46-130">Ces deux comportements garantissent que tous les appels sur les interfaces COM entre les objets gérés au-delà des limites du domaine d’application utilisent COM et COM Interop au lieu de la communication à distance.</span><span class="sxs-lookup"><span data-stu-id="6ee46-130">These two behaviors ensure that all calls over COM interfaces between managed objects across application domain boundaries use COM and COM interop instead of remoting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ee46-131">Exemple</span><span class="sxs-lookup"><span data-stu-id="6ee46-131">Example</span></span>  

 <span data-ttu-id="6ee46-132">L’exemple suivant montre comment spécifier que le runtime doit utiliser COM Interop à travers les limites d’isolation :</span><span class="sxs-lookup"><span data-stu-id="6ee46-132">The following example shows how to specify that the runtime should use COM interop across isolation boundaries:</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6ee46-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6ee46-133">See also</span></span>

- [<span data-ttu-id="6ee46-134">Schéma des paramètres d'exécution</span><span class="sxs-lookup"><span data-stu-id="6ee46-134">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="6ee46-135">Schéma du fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="6ee46-135">Configuration File Schema</span></span>](../index.md)
