---
title: <module>, élément (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#module
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/module
helpviewer_keywords:
- module element
- <module> element
ms.assetid: 10318725-9666-4d65-ab61-b94c64e59f13
ms.openlocfilehash: 15f4d10a70dc3c6abd32869f5b7b0006a799b4bf
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698042"
---
# <a name="module-element-network-settings"></a><span data-ttu-id="8a0b6-102">\<module >, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="8a0b6-102">\<module> Element (Network Settings)</span></span>
<span data-ttu-id="8a0b6-103">Ajoute un nouveau module proxy à l'application.</span><span class="sxs-lookup"><span data-stu-id="8a0b6-103">Adds a new proxy module to the application.</span></span>  
  
[<span data-ttu-id="8a0b6-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="8a0b6-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="8a0b6-105">&nbsp; @ no__t-1[ **@no__t -4System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="8a0b6-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="8a0b6-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<defaultProxy >** ](defaultproxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="8a0b6-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>  
<span data-ttu-id="8a0b6-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<module >**</span><span class="sxs-lookup"><span data-stu-id="8a0b6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<module>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a0b6-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8a0b6-108">Syntax</span></span>  
  
```xml  
<module   
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8a0b6-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="8a0b6-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8a0b6-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="8a0b6-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8a0b6-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="8a0b6-111">Attributes</span></span>  
  
|<span data-ttu-id="8a0b6-112">**Attribut**</span><span class="sxs-lookup"><span data-stu-id="8a0b6-112">**Attribute**</span></span>|<span data-ttu-id="8a0b6-113">**Description**</span><span class="sxs-lookup"><span data-stu-id="8a0b6-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="8a0b6-114">Le nom de type qualifié complet (indiqué par la propriété <xref:System.Type.FullName%2A>) et le nom de l’assembly (indiqué par la propriété <xref:System.Reflection.Assembly.FullName%2A>), séparés par une virgule, qui implémente le proxy.</span><span class="sxs-lookup"><span data-stu-id="8a0b6-114">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements the proxy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8a0b6-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8a0b6-115">Child Elements</span></span>  
 <span data-ttu-id="8a0b6-116">Aucun.</span><span class="sxs-lookup"><span data-stu-id="8a0b6-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8a0b6-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="8a0b6-117">Parent Elements</span></span>  
  
|<span data-ttu-id="8a0b6-118">**Élément**</span><span class="sxs-lookup"><span data-stu-id="8a0b6-118">**Element**</span></span>|<span data-ttu-id="8a0b6-119">**Description**</span><span class="sxs-lookup"><span data-stu-id="8a0b6-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="8a0b6-120">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="8a0b6-120">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="8a0b6-121">Configure le serveur proxy HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="8a0b6-121">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8a0b6-122">Notes</span><span class="sxs-lookup"><span data-stu-id="8a0b6-122">Remarks</span></span>  
 <span data-ttu-id="8a0b6-123">L’élément `module` inscrit les classes proxy qui implémentent l’interface <xref:System.Net.IWebProxy>.</span><span class="sxs-lookup"><span data-stu-id="8a0b6-123">The `module` element registers proxy classes that implement the <xref:System.Net.IWebProxy> interface.</span></span> <span data-ttu-id="8a0b6-124">Après l’inscription de la classe proxy, `module` peut être utilisé pour demander des informations par le biais du proxy pris en charge.</span><span class="sxs-lookup"><span data-stu-id="8a0b6-124">After registering the proxy class, `module` can be used to request information through the supported proxy.</span></span>  
  
 <span data-ttu-id="8a0b6-125">La valeur de l’attribut `type` doit être le nom de classe du module et le nom de la bibliothèque de liens dynamiques (DLL) correspondante.</span><span class="sxs-lookup"><span data-stu-id="8a0b6-125">The value for the `type` attribute should be the class name of the module and the name of its corresponding Dynamic Link Library (DLL).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="8a0b6-126">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="8a0b6-126">Configuration Files</span></span>  
 <span data-ttu-id="8a0b6-127">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="8a0b6-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a0b6-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="8a0b6-128">Example</span></span>  
 <span data-ttu-id="8a0b6-129">L’exemple suivant inscrit une classe proxy personnalisée.</span><span class="sxs-lookup"><span data-stu-id="8a0b6-129">The following example registers a custom proxy class.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <module  
        type="Test.CustomWebProxy, TestProxy, Version=2.0.3600.0, Culture=neutral, PublicKeyToken=b23a5c561934e385"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8a0b6-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8a0b6-130">See also</span></span>

- <xref:System.Net.IWebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="8a0b6-131">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="8a0b6-131">Network Settings Schema</span></span>](index.md)
