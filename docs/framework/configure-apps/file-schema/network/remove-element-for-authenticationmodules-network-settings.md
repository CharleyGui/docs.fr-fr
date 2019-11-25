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
ms.openlocfilehash: 2113b2b81ae347b398b0f25028dc6c361aec8447
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089180"
---
# <a name="remove-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="5a5d1-102">\<supprimer > élément pour authenticationModules (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="5a5d1-102">\<remove> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="5a5d1-103">Supprime un module d’authentification de l’application.</span><span class="sxs-lookup"><span data-stu-id="5a5d1-103">Removes an authentication module from the application.</span></span>  

<span data-ttu-id="5a5d1-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5a5d1-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5a5d1-105">&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="5a5d1-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="5a5d1-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<authenticationModules**](authenticationmodules-element-network-settings.md) ></span><span class="sxs-lookup"><span data-stu-id="5a5d1-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)</span></span>\
<span data-ttu-id="5a5d1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**supprimer >**</span><span class="sxs-lookup"><span data-stu-id="5a5d1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="5a5d1-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a5d1-108">Syntax</span></span>  
  
```xml  
<remove   
   type="authentication module name"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5a5d1-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5a5d1-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5a5d1-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="5a5d1-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5a5d1-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="5a5d1-111">Attributes</span></span>  
  
|<span data-ttu-id="5a5d1-112">**Attribut**</span><span class="sxs-lookup"><span data-stu-id="5a5d1-112">**Attribute**</span></span>|<span data-ttu-id="5a5d1-113">**Description**</span><span class="sxs-lookup"><span data-stu-id="5a5d1-113">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="5a5d1-114">**type**</span><span class="sxs-lookup"><span data-stu-id="5a5d1-114">**type**</span></span>|<span data-ttu-id="5a5d1-115">Nom du module d’authentification à supprimer.</span><span class="sxs-lookup"><span data-stu-id="5a5d1-115">The name of the authentication module to remove.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5a5d1-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5a5d1-116">Child Elements</span></span>  
 <span data-ttu-id="5a5d1-117">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="5a5d1-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5a5d1-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5a5d1-118">Parent Elements</span></span>  
  
|<span data-ttu-id="5a5d1-119">**Élément**</span><span class="sxs-lookup"><span data-stu-id="5a5d1-119">**Element**</span></span>|<span data-ttu-id="5a5d1-120">**Description**</span><span class="sxs-lookup"><span data-stu-id="5a5d1-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="5a5d1-121">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="5a5d1-121">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="5a5d1-122">Spécifie les modules utilisés pour authentifier les demandes réseau.</span><span class="sxs-lookup"><span data-stu-id="5a5d1-122">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a5d1-123">Notes</span><span class="sxs-lookup"><span data-stu-id="5a5d1-123">Remarks</span></span>  
 <span data-ttu-id="5a5d1-124">L’élément `remove` supprime les modules d’authentification qui ont été définis précédemment dans le fichier de configuration ou à un niveau supérieur dans la hiérarchie de configuration.</span><span class="sxs-lookup"><span data-stu-id="5a5d1-124">The `remove` element removes authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
 <span data-ttu-id="5a5d1-125">La valeur de l’attribut `type` doit être un nom de classe valide.</span><span class="sxs-lookup"><span data-stu-id="5a5d1-125">The value for the `type` attribute should be a valid class name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="5a5d1-126">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="5a5d1-126">Configuration Files</span></span>  
 <span data-ttu-id="5a5d1-127">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="5a5d1-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a5d1-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="5a5d1-128">Example</span></span>  
 <span data-ttu-id="5a5d1-129">L’exemple suivant supprime un module d’authentification.</span><span class="sxs-lookup"><span data-stu-id="5a5d1-129">The following example removes an authentication module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <remove type="System.Net.NtlmClient" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5a5d1-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5a5d1-130">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="5a5d1-131">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="5a5d1-131">Network Settings Schema</span></span>](index.md)
