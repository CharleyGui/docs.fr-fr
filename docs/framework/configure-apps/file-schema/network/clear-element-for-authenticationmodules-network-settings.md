---
title: <clear>, élément d’authenticationModules (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- clear element, authenticationModules
- <authenticationModules>, clear element
- <clear> element, authenticationModules
- authenticationModules, clear element
ms.assetid: dc522c45-4a80-4831-8955-f7b68a47edfd
ms.openlocfilehash: 6ac2287ba9b17727835d43a3e3b8876f210fb5c7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167325"
---
# <a name="clear-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="97bac-102">\<clear>, élément d’authenticationModules (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="97bac-102">\<clear> Element for authenticationModules (Network Settings)</span></span>

<span data-ttu-id="97bac-103">Efface tous les modules d’authentification de l’application.</span><span class="sxs-lookup"><span data-stu-id="97bac-103">Clears all authentication modules from the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="97bac-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="97bac-104">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="97bac-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="97bac-105">Attributes and Elements</span></span>  

 <span data-ttu-id="97bac-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="97bac-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="97bac-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="97bac-107">Attributes</span></span>  

 <span data-ttu-id="97bac-108">Aucun.</span><span class="sxs-lookup"><span data-stu-id="97bac-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="97bac-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="97bac-109">Child Elements</span></span>  

 <span data-ttu-id="97bac-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="97bac-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="97bac-111">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="97bac-111">Parent Elements</span></span>  
  
|<span data-ttu-id="97bac-112">**Element**</span><span class="sxs-lookup"><span data-stu-id="97bac-112">**Element**</span></span>|<span data-ttu-id="97bac-113">**Description**</span><span class="sxs-lookup"><span data-stu-id="97bac-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="97bac-114">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="97bac-114">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="97bac-115">Spécifie les modules utilisés pour authentifier les demandes réseau.</span><span class="sxs-lookup"><span data-stu-id="97bac-115">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97bac-116">Notes</span><span class="sxs-lookup"><span data-stu-id="97bac-116">Remarks</span></span>  

 <span data-ttu-id="97bac-117">L' `clear` élément supprime tous les modules d’authentification qui ont été définis précédemment dans le fichier de configuration ou à un niveau supérieur dans la hiérarchie de configuration.</span><span class="sxs-lookup"><span data-stu-id="97bac-117">The `clear` element removes all authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="97bac-118">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="97bac-118">Configuration Files</span></span>  

 <span data-ttu-id="97bac-119">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="97bac-119">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="97bac-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="97bac-120">Example</span></span>  

 <span data-ttu-id="97bac-121">L’exemple suivant supprime tous les modules d’authentification configurés.</span><span class="sxs-lookup"><span data-stu-id="97bac-121">The following example removes all configured authentication modules.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <clear/>  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="97bac-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="97bac-122">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="97bac-123">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="97bac-123">Network Settings Schema</span></span>](index.md)
