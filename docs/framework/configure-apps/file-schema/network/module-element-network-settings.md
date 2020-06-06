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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154827"
---
# <a name="module-element-network-settings"></a><span data-ttu-id="db785-102">\<module>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="db785-102">\<module> Element (Network Settings)</span></span>
<span data-ttu-id="db785-103">Ajoute un nouveau module proxy à l'application.</span><span class="sxs-lookup"><span data-stu-id="db785-103">Adds a new proxy module to the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<module>**

## <a name="syntax"></a><span data-ttu-id="db785-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db785-104">Syntax</span></span>  
  
```xml  
<module
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="db785-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="db785-105">Attributes and Elements</span></span>  
 <span data-ttu-id="db785-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="db785-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="db785-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="db785-107">Attributes</span></span>  
  
|<span data-ttu-id="db785-108">**Attribut**</span><span class="sxs-lookup"><span data-stu-id="db785-108">**Attribute**</span></span>|<span data-ttu-id="db785-109">**Description**</span><span class="sxs-lookup"><span data-stu-id="db785-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="db785-110">Le nom de type qualifié complet (indiqué par la <xref:System.Type.FullName%2A> propriété) et le nom de l’assembly (indiqué par la <xref:System.Reflection.Assembly.FullName%2A> propriété), séparés par une virgule, qui implémente le proxy.</span><span class="sxs-lookup"><span data-stu-id="db785-110">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements the proxy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="db785-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="db785-111">Child Elements</span></span>  
 <span data-ttu-id="db785-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="db785-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="db785-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="db785-113">Parent Elements</span></span>  
  
|<span data-ttu-id="db785-114">**Appartient**</span><span class="sxs-lookup"><span data-stu-id="db785-114">**Element**</span></span>|<span data-ttu-id="db785-115">**Description**</span><span class="sxs-lookup"><span data-stu-id="db785-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="db785-116">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="db785-116">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="db785-117">Configure le serveur proxy HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="db785-117">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db785-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="db785-118">Remarks</span></span>  
 <span data-ttu-id="db785-119">L' `module` élément inscrit des classes proxy qui implémentent l' <xref:System.Net.IWebProxy> interface.</span><span class="sxs-lookup"><span data-stu-id="db785-119">The `module` element registers proxy classes that implement the <xref:System.Net.IWebProxy> interface.</span></span> <span data-ttu-id="db785-120">Après l’inscription de la classe proxy, `module` peut être utilisé pour demander des informations par le biais du proxy pris en charge.</span><span class="sxs-lookup"><span data-stu-id="db785-120">After registering the proxy class, `module` can be used to request information through the supported proxy.</span></span>  
  
 <span data-ttu-id="db785-121">La valeur de l' `type` attribut doit être le nom de classe du module et le nom de la bibliothèque de liens dynamiques (dll) correspondante.</span><span class="sxs-lookup"><span data-stu-id="db785-121">The value for the `type` attribute should be the class name of the module and the name of its corresponding Dynamic Link Library (DLL).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="db785-122">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="db785-122">Configuration Files</span></span>  
 <span data-ttu-id="db785-123">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="db785-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="db785-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="db785-124">Example</span></span>  
 <span data-ttu-id="db785-125">L’exemple suivant inscrit une classe proxy personnalisée.</span><span class="sxs-lookup"><span data-stu-id="db785-125">The following example registers a custom proxy class.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="db785-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="db785-126">See also</span></span>

- <xref:System.Net.IWebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="db785-127">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="db785-127">Network Settings Schema</span></span>](index.md)
