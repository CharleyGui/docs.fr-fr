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
ms.openlocfilehash: b502cc4a0958f074018d4b0ce6b3fb118b811c2f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154970"
---
# <a name="authenticationmodules-element-network-settings"></a><span data-ttu-id="9d46d-102">\<authenticationModules, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="9d46d-102">\<authenticationModules> Element (Network Settings)</span></span>
<span data-ttu-id="9d46d-103">Spécifie les modules utilisés pour authentifier les demandes de réseau.</span><span class="sxs-lookup"><span data-stu-id="9d46d-103">Specifies modules used to authenticate network requests.</span></span>  

<span data-ttu-id="9d46d-104">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9d46d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9d46d-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="9d46d-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="9d46d-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<authentificationModules>**</span><span class="sxs-lookup"><span data-stu-id="9d46d-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<authenticationModules>**</span></span>

## <a name="syntax"></a><span data-ttu-id="9d46d-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d46d-107">Syntax</span></span>  
  
```xml  
<authenticationModules>
</authenticationModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9d46d-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="9d46d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9d46d-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="9d46d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9d46d-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="9d46d-110">Attributes</span></span>  
 <span data-ttu-id="9d46d-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="9d46d-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9d46d-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9d46d-112">Child Elements</span></span>  
  
|<span data-ttu-id="9d46d-113">**Élément**</span><span class="sxs-lookup"><span data-stu-id="9d46d-113">**Element**</span></span>|<span data-ttu-id="9d46d-114">**Description**</span><span class="sxs-lookup"><span data-stu-id="9d46d-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="9d46d-115">ajouter</span><span class="sxs-lookup"><span data-stu-id="9d46d-115">add</span></span>](add-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="9d46d-116">Ajoute un module d’authentification à l’application.</span><span class="sxs-lookup"><span data-stu-id="9d46d-116">Adds an authentication module to the application.</span></span>|  
|[<span data-ttu-id="9d46d-117">Clair</span><span class="sxs-lookup"><span data-stu-id="9d46d-117">clear</span></span>](clear-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="9d46d-118">Efface tous les modules d’authentification de l’application.</span><span class="sxs-lookup"><span data-stu-id="9d46d-118">Clears all authentication modules from the application.</span></span>|  
|[<span data-ttu-id="9d46d-119">retirer</span><span class="sxs-lookup"><span data-stu-id="9d46d-119">remove</span></span>](remove-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="9d46d-120">Supprime un module d’authentification de l’application.</span><span class="sxs-lookup"><span data-stu-id="9d46d-120">Removes an authentication module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9d46d-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9d46d-121">Parent Elements</span></span>  
  
|<span data-ttu-id="9d46d-122">**Élément**</span><span class="sxs-lookup"><span data-stu-id="9d46d-122">**Element**</span></span>|<span data-ttu-id="9d46d-123">**Description**</span><span class="sxs-lookup"><span data-stu-id="9d46d-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="9d46d-124">system.net</span><span class="sxs-lookup"><span data-stu-id="9d46d-124">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="9d46d-125">Contient des paramètres qui spécifient la manière dont .NET Framework se connecte au réseau.</span><span class="sxs-lookup"><span data-stu-id="9d46d-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d46d-126">Notes </span><span class="sxs-lookup"><span data-stu-id="9d46d-126">Remarks</span></span>  
 <span data-ttu-id="9d46d-127">L’élément `authenticationModule` spécifie les modules d’authentification qui effectuent le processus d’authentification avec un serveur.</span><span class="sxs-lookup"><span data-stu-id="9d46d-127">The `authenticationModule` element specifies the authentication modules that conduct the authentication process with a server.</span></span> <span data-ttu-id="9d46d-128">Un module d’authentification doit implémenter l’interface. <xref:System.Net.IAuthenticationModule></span><span class="sxs-lookup"><span data-stu-id="9d46d-128">An authentication module must implement the <xref:System.Net.IAuthenticationModule> interface.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="9d46d-129">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="9d46d-129">Configuration Files</span></span>  
 <span data-ttu-id="9d46d-130">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="9d46d-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d46d-131"> Exemple</span><span class="sxs-lookup"><span data-stu-id="9d46d-131">Example</span></span>  
 <span data-ttu-id="9d46d-132">L’exemple suivant permet un module d’authentification.</span><span class="sxs-lookup"><span data-stu-id="9d46d-132">The following example enables an authentication module.</span></span> <span data-ttu-id="9d46d-133">Vous devez remplacer les valeurs de Version et PublicKeyToken par les valeurs correctes pour le module spécifié.</span><span class="sxs-lookup"><span data-stu-id="9d46d-133">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9d46d-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9d46d-134">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="9d46d-135">Paramètres réseau Schema</span><span class="sxs-lookup"><span data-stu-id="9d46d-135">Network Settings Schema</span></span>](index.md)
