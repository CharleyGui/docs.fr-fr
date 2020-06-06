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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154970"
---
# <a name="authenticationmodules-element-network-settings"></a><span data-ttu-id="b8a1b-102">\<authenticationModules>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="b8a1b-102">\<authenticationModules> Element (Network Settings)</span></span>
<span data-ttu-id="b8a1b-103">Spécifie les modules utilisés pour authentifier les demandes réseau.</span><span class="sxs-lookup"><span data-stu-id="b8a1b-103">Specifies modules used to authenticate network requests.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<authenticationModules>**

## <a name="syntax"></a><span data-ttu-id="b8a1b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8a1b-104">Syntax</span></span>  
  
```xml  
<authenticationModules>
</authenticationModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b8a1b-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b8a1b-105">Attributes and Elements</span></span>  
 <span data-ttu-id="b8a1b-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b8a1b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b8a1b-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="b8a1b-107">Attributes</span></span>  
 <span data-ttu-id="b8a1b-108">Aucun.</span><span class="sxs-lookup"><span data-stu-id="b8a1b-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b8a1b-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b8a1b-109">Child Elements</span></span>  
  
|<span data-ttu-id="b8a1b-110">**Appartient**</span><span class="sxs-lookup"><span data-stu-id="b8a1b-110">**Element**</span></span>|<span data-ttu-id="b8a1b-111">**Description**</span><span class="sxs-lookup"><span data-stu-id="b8a1b-111">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b8a1b-112">add</span><span class="sxs-lookup"><span data-stu-id="b8a1b-112">add</span></span>](add-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="b8a1b-113">Ajoute un module d’authentification à l’application.</span><span class="sxs-lookup"><span data-stu-id="b8a1b-113">Adds an authentication module to the application.</span></span>|  
|[<span data-ttu-id="b8a1b-114">clear</span><span class="sxs-lookup"><span data-stu-id="b8a1b-114">clear</span></span>](clear-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="b8a1b-115">Efface tous les modules d’authentification de l’application.</span><span class="sxs-lookup"><span data-stu-id="b8a1b-115">Clears all authentication modules from the application.</span></span>|  
|[<span data-ttu-id="b8a1b-116">remove</span><span class="sxs-lookup"><span data-stu-id="b8a1b-116">remove</span></span>](remove-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="b8a1b-117">Supprime un module d’authentification de l’application.</span><span class="sxs-lookup"><span data-stu-id="b8a1b-117">Removes an authentication module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b8a1b-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b8a1b-118">Parent Elements</span></span>  
  
|<span data-ttu-id="b8a1b-119">**Appartient**</span><span class="sxs-lookup"><span data-stu-id="b8a1b-119">**Element**</span></span>|<span data-ttu-id="b8a1b-120">**Description**</span><span class="sxs-lookup"><span data-stu-id="b8a1b-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b8a1b-121">system.net</span><span class="sxs-lookup"><span data-stu-id="b8a1b-121">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="b8a1b-122">Contient des paramètres qui spécifient la manière dont .NET Framework se connecte au réseau.</span><span class="sxs-lookup"><span data-stu-id="b8a1b-122">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8a1b-123">Remarques</span><span class="sxs-lookup"><span data-stu-id="b8a1b-123">Remarks</span></span>  
 <span data-ttu-id="b8a1b-124">L' `authenticationModule` élément spécifie les modules d’authentification qui exécutent le processus d’authentification avec un serveur.</span><span class="sxs-lookup"><span data-stu-id="b8a1b-124">The `authenticationModule` element specifies the authentication modules that conduct the authentication process with a server.</span></span> <span data-ttu-id="b8a1b-125">Un module d’authentification doit implémenter l' <xref:System.Net.IAuthenticationModule> interface.</span><span class="sxs-lookup"><span data-stu-id="b8a1b-125">An authentication module must implement the <xref:System.Net.IAuthenticationModule> interface.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="b8a1b-126">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="b8a1b-126">Configuration Files</span></span>  
 <span data-ttu-id="b8a1b-127">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="b8a1b-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8a1b-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="b8a1b-128">Example</span></span>  
 <span data-ttu-id="b8a1b-129">L’exemple suivant active un module d’authentification.</span><span class="sxs-lookup"><span data-stu-id="b8a1b-129">The following example enables an authentication module.</span></span> <span data-ttu-id="b8a1b-130">Vous devez remplacer les valeurs de version et PublicKeyToken par les valeurs correctes pour le module spécifié.</span><span class="sxs-lookup"><span data-stu-id="b8a1b-130">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b8a1b-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b8a1b-131">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="b8a1b-132">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="b8a1b-132">Network Settings Schema</span></span>](index.md)
