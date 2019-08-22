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
ms.openlocfilehash: 12ac146926103b40073d34f48895b0645c8a8ed2
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659464"
---
# <a name="clear-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="f51e2-102">\<Clear > élément pour authenticationModules (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="f51e2-102">\<clear> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="f51e2-103">Efface tous les modules d’authentification de l’application.</span><span class="sxs-lookup"><span data-stu-id="f51e2-103">Clears all authentication modules from the application.</span></span>  
  
 <span data-ttu-id="f51e2-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="f51e2-104">\<configuration></span></span>  
<span data-ttu-id="f51e2-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="f51e2-105">\<system.net></span></span>  
<span data-ttu-id="f51e2-106">\<authenticationModules></span><span class="sxs-lookup"><span data-stu-id="f51e2-106">\<authenticationModules></span></span>  
<span data-ttu-id="f51e2-107">\<clear></span><span class="sxs-lookup"><span data-stu-id="f51e2-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f51e2-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f51e2-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f51e2-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f51e2-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f51e2-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f51e2-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f51e2-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="f51e2-111">Attributes</span></span>  
 <span data-ttu-id="f51e2-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="f51e2-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f51e2-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f51e2-113">Child Elements</span></span>  
 <span data-ttu-id="f51e2-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="f51e2-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f51e2-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f51e2-115">Parent Elements</span></span>  
  
|<span data-ttu-id="f51e2-116">**Élément**</span><span class="sxs-lookup"><span data-stu-id="f51e2-116">**Element**</span></span>|<span data-ttu-id="f51e2-117">**Description**</span><span class="sxs-lookup"><span data-stu-id="f51e2-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="f51e2-118">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="f51e2-118">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="f51e2-119">Spécifie les modules utilisés pour authentifier les demandes réseau.</span><span class="sxs-lookup"><span data-stu-id="f51e2-119">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f51e2-120">Notes</span><span class="sxs-lookup"><span data-stu-id="f51e2-120">Remarks</span></span>  
 <span data-ttu-id="f51e2-121">L' `clear` élément supprime tous les modules d’authentification qui ont été définis précédemment dans le fichier de configuration ou à un niveau supérieur dans la hiérarchie de configuration.</span><span class="sxs-lookup"><span data-stu-id="f51e2-121">The `clear` element removes all authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="f51e2-122">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="f51e2-122">Configuration Files</span></span>  
 <span data-ttu-id="f51e2-123">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="f51e2-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f51e2-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="f51e2-124">Example</span></span>  
 <span data-ttu-id="f51e2-125">L’exemple suivant supprime tous les modules d’authentification configurés.</span><span class="sxs-lookup"><span data-stu-id="f51e2-125">The following example removes all configured authentication modules.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <clear/>  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f51e2-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f51e2-126">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="f51e2-127">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="f51e2-127">Network Settings Schema</span></span>](index.md)
