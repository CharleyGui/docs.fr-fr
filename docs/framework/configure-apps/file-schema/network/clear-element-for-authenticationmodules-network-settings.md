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
ms.openlocfilehash: 052f7eef30500d37389585956728250a46b718a3
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698399"
---
# <a name="clear-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="97ea7-102">\<clear > élément pour authenticationModules (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="97ea7-102">\<clear> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="97ea7-103">Efface tous les modules d’authentification de l’application.</span><span class="sxs-lookup"><span data-stu-id="97ea7-103">Clears all authentication modules from the application.</span></span>  
  
[<span data-ttu-id="97ea7-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="97ea7-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="97ea7-105">&nbsp; @ no__t-1[ **@no__t -4System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="97ea7-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="97ea7-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<authenticationModules >** ](authenticationmodules-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="97ea7-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)</span></span>  
<span data-ttu-id="97ea7-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<clear >**</span><span class="sxs-lookup"><span data-stu-id="97ea7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97ea7-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="97ea7-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="97ea7-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="97ea7-109">Attributes and Elements</span></span>  
 <span data-ttu-id="97ea7-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="97ea7-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="97ea7-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="97ea7-111">Attributes</span></span>  
 <span data-ttu-id="97ea7-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="97ea7-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="97ea7-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="97ea7-113">Child Elements</span></span>  
 <span data-ttu-id="97ea7-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="97ea7-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="97ea7-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="97ea7-115">Parent Elements</span></span>  
  
|<span data-ttu-id="97ea7-116">**Élément**</span><span class="sxs-lookup"><span data-stu-id="97ea7-116">**Element**</span></span>|<span data-ttu-id="97ea7-117">**Description**</span><span class="sxs-lookup"><span data-stu-id="97ea7-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="97ea7-118">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="97ea7-118">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="97ea7-119">Spécifie les modules utilisés pour authentifier les demandes réseau.</span><span class="sxs-lookup"><span data-stu-id="97ea7-119">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97ea7-120">Notes</span><span class="sxs-lookup"><span data-stu-id="97ea7-120">Remarks</span></span>  
 <span data-ttu-id="97ea7-121">L’élément `clear` supprime tous les modules d’authentification qui ont été définis précédemment dans le fichier de configuration ou à un niveau supérieur dans la hiérarchie de configuration.</span><span class="sxs-lookup"><span data-stu-id="97ea7-121">The `clear` element removes all authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="97ea7-122">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="97ea7-122">Configuration Files</span></span>  
 <span data-ttu-id="97ea7-123">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="97ea7-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="97ea7-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="97ea7-124">Example</span></span>  
 <span data-ttu-id="97ea7-125">L’exemple suivant supprime tous les modules d’authentification configurés.</span><span class="sxs-lookup"><span data-stu-id="97ea7-125">The following example removes all configured authentication modules.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <clear/>  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="97ea7-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="97ea7-126">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="97ea7-127">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="97ea7-127">Network Settings Schema</span></span>](index.md)
