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
ms.openlocfilehash: ed28ae4a52085cbfa781b4baf2ee1eafbeff6eb4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154827"
---
# <a name="module-element-network-settings"></a><span data-ttu-id="5be85-102">\<module> Element (Paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="5be85-102">\<module> Element (Network Settings)</span></span>
<span data-ttu-id="5be85-103">Ajoute un nouveau module proxy à l'application.</span><span class="sxs-lookup"><span data-stu-id="5be85-103">Adds a new proxy module to the application.</span></span>  

<span data-ttu-id="5be85-104">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5be85-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5be85-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="5be85-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="5be85-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<défautProxy>**](defaultproxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="5be85-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>\
<span data-ttu-id="5be85-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<module>**</span><span class="sxs-lookup"><span data-stu-id="5be85-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<module>**</span></span>

## <a name="syntax"></a><span data-ttu-id="5be85-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5be85-108">Syntax</span></span>  
  
```xml  
<module
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5be85-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5be85-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5be85-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="5be85-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5be85-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="5be85-111">Attributes</span></span>  
  
|<span data-ttu-id="5be85-112">**Attribut**</span><span class="sxs-lookup"><span data-stu-id="5be85-112">**Attribute**</span></span>|<span data-ttu-id="5be85-113">**Description**</span><span class="sxs-lookup"><span data-stu-id="5be85-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="5be85-114">Le nom de type entièrement <xref:System.Type.FullName%2A> qualifié (indiqué par la <xref:System.Reflection.Assembly.FullName%2A> propriété) et le nom d’assemblage (indiqué par la propriété), séparés par une virgule, qui implémente le proxy.</span><span class="sxs-lookup"><span data-stu-id="5be85-114">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements the proxy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5be85-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5be85-115">Child Elements</span></span>  
 <span data-ttu-id="5be85-116">Aucun.</span><span class="sxs-lookup"><span data-stu-id="5be85-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5be85-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5be85-117">Parent Elements</span></span>  
  
|<span data-ttu-id="5be85-118">**Élément**</span><span class="sxs-lookup"><span data-stu-id="5be85-118">**Element**</span></span>|<span data-ttu-id="5be85-119">**Description**</span><span class="sxs-lookup"><span data-stu-id="5be85-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="5be85-120">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="5be85-120">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="5be85-121">Configure le serveur proxy HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="5be85-121">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5be85-122">Notes </span><span class="sxs-lookup"><span data-stu-id="5be85-122">Remarks</span></span>  
 <span data-ttu-id="5be85-123">L’élément `module` enregistre les classes <xref:System.Net.IWebProxy> proxy qui implémenter l’interface.</span><span class="sxs-lookup"><span data-stu-id="5be85-123">The `module` element registers proxy classes that implement the <xref:System.Net.IWebProxy> interface.</span></span> <span data-ttu-id="5be85-124">Après l’enregistrement de `module` la classe de procuration, peut être utilisé pour demander des informations par l’intermédiaire de la procuration prise en charge.</span><span class="sxs-lookup"><span data-stu-id="5be85-124">After registering the proxy class, `module` can be used to request information through the supported proxy.</span></span>  
  
 <span data-ttu-id="5be85-125">La valeur `type` de l’attribut doit être le nom de classe du module et le nom de sa bibliothèque dynamique correspondante (DLL).</span><span class="sxs-lookup"><span data-stu-id="5be85-125">The value for the `type` attribute should be the class name of the module and the name of its corresponding Dynamic Link Library (DLL).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="5be85-126">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="5be85-126">Configuration Files</span></span>  
 <span data-ttu-id="5be85-127">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="5be85-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5be85-128"> Exemple</span><span class="sxs-lookup"><span data-stu-id="5be85-128">Example</span></span>  
 <span data-ttu-id="5be85-129">L’exemple suivant enregistre une classe de proxy personnalisée.</span><span class="sxs-lookup"><span data-stu-id="5be85-129">The following example registers a custom proxy class.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5be85-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5be85-130">See also</span></span>

- <xref:System.Net.IWebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="5be85-131">Paramètres réseau Schema</span><span class="sxs-lookup"><span data-stu-id="5be85-131">Network Settings Schema</span></span>](index.md)
