---
title: <remove>, élément d’authenticationModules (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- remove element, authenticationModules
- <authenticationModules>, remove element
- <remove> element, authenticationModules
- authenticationModules, remove element
ms.assetid: abf79949-b05c-465a-b51c-bbeda9a74173
ms.openlocfilehash: d171fea193bbae068e69b8976abb8e56a5623f02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154775"
---
# <a name="remove-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="086be-102">\<supprimer> Element pour l’authentificationModules (Paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="086be-102">\<remove> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="086be-103">Supprime un module d’authentification de l’application.</span><span class="sxs-lookup"><span data-stu-id="086be-103">Removes an authentication module from the application.</span></span>  

<span data-ttu-id="086be-104">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="086be-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="086be-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="086be-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="086be-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<authentificationModules>**](authenticationmodules-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="086be-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)</span></span>\
<span data-ttu-id="086be-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<supprimer>**</span><span class="sxs-lookup"><span data-stu-id="086be-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="086be-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="086be-108">Syntax</span></span>  
  
```xml  
<remove
   type="authentication module name"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="086be-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="086be-109">Attributes and Elements</span></span>  
 <span data-ttu-id="086be-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="086be-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="086be-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="086be-111">Attributes</span></span>  
  
|<span data-ttu-id="086be-112">**Attribut**</span><span class="sxs-lookup"><span data-stu-id="086be-112">**Attribute**</span></span>|<span data-ttu-id="086be-113">**Description**</span><span class="sxs-lookup"><span data-stu-id="086be-113">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="086be-114">**type**</span><span class="sxs-lookup"><span data-stu-id="086be-114">**type**</span></span>|<span data-ttu-id="086be-115">Le nom du module d’authentification à supprimer.</span><span class="sxs-lookup"><span data-stu-id="086be-115">The name of the authentication module to remove.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="086be-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="086be-116">Child Elements</span></span>  
 <span data-ttu-id="086be-117">Aucun.</span><span class="sxs-lookup"><span data-stu-id="086be-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="086be-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="086be-118">Parent Elements</span></span>  
  
|<span data-ttu-id="086be-119">**Élément**</span><span class="sxs-lookup"><span data-stu-id="086be-119">**Element**</span></span>|<span data-ttu-id="086be-120">**Description**</span><span class="sxs-lookup"><span data-stu-id="086be-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="086be-121">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="086be-121">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="086be-122">Spécifie les modules utilisés pour authentifier les demandes de réseau.</span><span class="sxs-lookup"><span data-stu-id="086be-122">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="086be-123">Notes </span><span class="sxs-lookup"><span data-stu-id="086be-123">Remarks</span></span>  
 <span data-ttu-id="086be-124">L’élément `remove` supprime les modules d’authentification qui ont été définis plus tôt dans le fichier de configuration ou à un niveau supérieur dans la hiérarchie de configuration.</span><span class="sxs-lookup"><span data-stu-id="086be-124">The `remove` element removes authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
 <span data-ttu-id="086be-125">La valeur `type` de l’attribut doit être un nom de classe valide.</span><span class="sxs-lookup"><span data-stu-id="086be-125">The value for the `type` attribute should be a valid class name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="086be-126">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="086be-126">Configuration Files</span></span>  
 <span data-ttu-id="086be-127">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="086be-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="086be-128"> Exemple</span><span class="sxs-lookup"><span data-stu-id="086be-128">Example</span></span>  
 <span data-ttu-id="086be-129">L’exemple suivant supprime un module d’authentification.</span><span class="sxs-lookup"><span data-stu-id="086be-129">The following example removes an authentication module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <remove type="System.Net.NtlmClient" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="086be-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="086be-130">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="086be-131">Paramètres réseau Schema</span><span class="sxs-lookup"><span data-stu-id="086be-131">Network Settings Schema</span></span>](index.md)
