---
title: <authenticationModules>, élément (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#authenticationModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules
helpviewer_keywords:
- authenticationModules element
- <authenticationModules> element
ms.assetid: 10fcfaad-82ef-4692-871a-0aec9dfbe75e
ms.openlocfilehash: 4fe44deba951e5302518ed855589ad1b0ca75343
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699532"
---
# <a name="authenticationmodules-element-network-settings"></a><span data-ttu-id="b8011-102">\<authenticationModules >, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="b8011-102">\<authenticationModules> Element (Network Settings)</span></span>
<span data-ttu-id="b8011-103">Spécifie les modules utilisés pour authentifier les demandes réseau.</span><span class="sxs-lookup"><span data-stu-id="b8011-103">Specifies modules used to authenticate network requests.</span></span>  
  
[<span data-ttu-id="b8011-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="b8011-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="b8011-105">&nbsp; @ no__t-1[ **@no__t -4System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="b8011-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="b8011-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<authenticationModules >**</span><span class="sxs-lookup"><span data-stu-id="b8011-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<authenticationModules>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8011-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8011-107">Syntax</span></span>  
  
```xml  
<authenticationModules>   
</authenticationModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b8011-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b8011-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b8011-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b8011-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b8011-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="b8011-110">Attributes</span></span>  
 <span data-ttu-id="b8011-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="b8011-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b8011-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b8011-112">Child Elements</span></span>  
  
|<span data-ttu-id="b8011-113">**Élément**</span><span class="sxs-lookup"><span data-stu-id="b8011-113">**Element**</span></span>|<span data-ttu-id="b8011-114">**Description**</span><span class="sxs-lookup"><span data-stu-id="b8011-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b8011-115">add</span><span class="sxs-lookup"><span data-stu-id="b8011-115">add</span></span>](add-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="b8011-116">Ajoute un module d’authentification à l’application.</span><span class="sxs-lookup"><span data-stu-id="b8011-116">Adds an authentication module to the application.</span></span>|  
|[<span data-ttu-id="b8011-117">clear</span><span class="sxs-lookup"><span data-stu-id="b8011-117">clear</span></span>](clear-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="b8011-118">Efface tous les modules d’authentification de l’application.</span><span class="sxs-lookup"><span data-stu-id="b8011-118">Clears all authentication modules from the application.</span></span>|  
|[<span data-ttu-id="b8011-119">remove</span><span class="sxs-lookup"><span data-stu-id="b8011-119">remove</span></span>](remove-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="b8011-120">Supprime un module d’authentification de l’application.</span><span class="sxs-lookup"><span data-stu-id="b8011-120">Removes an authentication module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b8011-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b8011-121">Parent Elements</span></span>  
  
|<span data-ttu-id="b8011-122">**Élément**</span><span class="sxs-lookup"><span data-stu-id="b8011-122">**Element**</span></span>|<span data-ttu-id="b8011-123">**Description**</span><span class="sxs-lookup"><span data-stu-id="b8011-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b8011-124">system.net</span><span class="sxs-lookup"><span data-stu-id="b8011-124">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="b8011-125">Contient des paramètres qui spécifient la manière dont .NET Framework se connecte au réseau.</span><span class="sxs-lookup"><span data-stu-id="b8011-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8011-126">Notes</span><span class="sxs-lookup"><span data-stu-id="b8011-126">Remarks</span></span>  
 <span data-ttu-id="b8011-127">L’élément `authenticationModule` spécifie les modules d’authentification qui exécutent le processus d’authentification avec un serveur.</span><span class="sxs-lookup"><span data-stu-id="b8011-127">The `authenticationModule` element specifies the authentication modules that conduct the authentication process with a server.</span></span> <span data-ttu-id="b8011-128">Un module d’authentification doit implémenter l’interface <xref:System.Net.IAuthenticationModule>.</span><span class="sxs-lookup"><span data-stu-id="b8011-128">An authentication module must implement the <xref:System.Net.IAuthenticationModule> interface.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="b8011-129">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="b8011-129">Configuration Files</span></span>  
 <span data-ttu-id="b8011-130">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="b8011-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8011-131">Exemple</span><span class="sxs-lookup"><span data-stu-id="b8011-131">Example</span></span>  
 <span data-ttu-id="b8011-132">L’exemple suivant active un module d’authentification.</span><span class="sxs-lookup"><span data-stu-id="b8011-132">The following example enables an authentication module.</span></span> <span data-ttu-id="b8011-133">Vous devez remplacer les valeurs de version et PublicKeyToken par les valeurs correctes pour le module spécifié.</span><span class="sxs-lookup"><span data-stu-id="b8011-133">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <add type="System.Net.DigestClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b8011-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b8011-134">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="b8011-135">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="b8011-135">Network Settings Schema</span></span>](index.md)
