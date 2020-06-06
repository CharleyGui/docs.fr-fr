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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154775"
---
# <a name="remove-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="1b12e-102">\<remove>, élément d’authenticationModules (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="1b12e-102">\<remove> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="1b12e-103">Supprime un module d’authentification de l’application.</span><span class="sxs-lookup"><span data-stu-id="1b12e-103">Removes an authentication module from the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="1b12e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1b12e-104">Syntax</span></span>  
  
```xml  
<remove
   type="authentication module name"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1b12e-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="1b12e-105">Attributes and Elements</span></span>  
 <span data-ttu-id="1b12e-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="1b12e-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1b12e-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="1b12e-107">Attributes</span></span>  
  
|<span data-ttu-id="1b12e-108">**Attribut**</span><span class="sxs-lookup"><span data-stu-id="1b12e-108">**Attribute**</span></span>|<span data-ttu-id="1b12e-109">**Description**</span><span class="sxs-lookup"><span data-stu-id="1b12e-109">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="1b12e-110">**type**</span><span class="sxs-lookup"><span data-stu-id="1b12e-110">**type**</span></span>|<span data-ttu-id="1b12e-111">Nom du module d’authentification à supprimer.</span><span class="sxs-lookup"><span data-stu-id="1b12e-111">The name of the authentication module to remove.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1b12e-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1b12e-112">Child Elements</span></span>  
 <span data-ttu-id="1b12e-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="1b12e-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1b12e-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1b12e-114">Parent Elements</span></span>  
  
|<span data-ttu-id="1b12e-115">**Appartient**</span><span class="sxs-lookup"><span data-stu-id="1b12e-115">**Element**</span></span>|<span data-ttu-id="1b12e-116">**Description**</span><span class="sxs-lookup"><span data-stu-id="1b12e-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="1b12e-117">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="1b12e-117">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="1b12e-118">Spécifie les modules utilisés pour authentifier les demandes réseau.</span><span class="sxs-lookup"><span data-stu-id="1b12e-118">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b12e-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="1b12e-119">Remarks</span></span>  
 <span data-ttu-id="1b12e-120">L' `remove` élément supprime les modules d’authentification qui ont été définis précédemment dans le fichier de configuration ou à un niveau supérieur dans la hiérarchie de configuration.</span><span class="sxs-lookup"><span data-stu-id="1b12e-120">The `remove` element removes authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
 <span data-ttu-id="1b12e-121">La valeur de l' `type` attribut doit être un nom de classe valide.</span><span class="sxs-lookup"><span data-stu-id="1b12e-121">The value for the `type` attribute should be a valid class name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="1b12e-122">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="1b12e-122">Configuration Files</span></span>  
 <span data-ttu-id="1b12e-123">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="1b12e-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b12e-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="1b12e-124">Example</span></span>  
 <span data-ttu-id="1b12e-125">L’exemple suivant supprime un module d’authentification.</span><span class="sxs-lookup"><span data-stu-id="1b12e-125">The following example removes an authentication module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <remove type="System.Net.NtlmClient" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1b12e-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1b12e-126">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="1b12e-127">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="1b12e-127">Network Settings Schema</span></span>](index.md)
