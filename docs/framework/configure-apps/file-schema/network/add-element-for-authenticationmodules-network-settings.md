---
title: <add>, élément d’authenticationModules (paramètres réseau)
description: L' <add> élément paramètres réseau pour connectionManagement ajoute une adresse IP ou un nom DNS à la liste de gestion des connexions dans la .NET Framework.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/add
helpviewer_keywords:
- authenticationModules, add element
- add element, authenticationModules
- <authenticationModules>, add element
- <add> element, authenticationModules
ms.assetid: 333c5fb0-a2ab-4db8-8531-a7fe37bb9b5b
ms.openlocfilehash: f679a43ed1851e9681a2a57ca1639f8aa75aa8b3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149502"
---
# <a name="add-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="4cdde-103">\<add>, élément d’authenticationModules (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="4cdde-103">\<add> Element for authenticationModules (Network Settings)</span></span>

<span data-ttu-id="4cdde-104">Ajoute un module d’authentification à l’application.</span><span class="sxs-lookup"><span data-stu-id="4cdde-104">Adds an authentication module to the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="4cdde-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4cdde-105">Syntax</span></span>  
  
```xml  
<add
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4cdde-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="4cdde-106">Attributes and Elements</span></span>  

 <span data-ttu-id="4cdde-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="4cdde-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4cdde-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="4cdde-108">Attributes</span></span>  
  
|<span data-ttu-id="4cdde-109">**Attribut**</span><span class="sxs-lookup"><span data-stu-id="4cdde-109">**Attribute**</span></span>|<span data-ttu-id="4cdde-110">**Description**</span><span class="sxs-lookup"><span data-stu-id="4cdde-110">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="4cdde-111">Nom de type qualifié complet (indiqué par la <xref:System.Type.FullName%2A> propriété) et nom de l’assembly (indiqué par la <xref:System.Reflection.Assembly.FullName%2A> propriété), séparés par une virgule.</span><span class="sxs-lookup"><span data-stu-id="4cdde-111">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4cdde-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4cdde-112">Child Elements</span></span>  

 <span data-ttu-id="4cdde-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="4cdde-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4cdde-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4cdde-114">Parent Elements</span></span>  
  
|<span data-ttu-id="4cdde-115">**Element**</span><span class="sxs-lookup"><span data-stu-id="4cdde-115">**Element**</span></span>|<span data-ttu-id="4cdde-116">**Description**</span><span class="sxs-lookup"><span data-stu-id="4cdde-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="4cdde-117">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="4cdde-117">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="4cdde-118">Spécifie les modules utilisés pour authentifier les demandes réseau.</span><span class="sxs-lookup"><span data-stu-id="4cdde-118">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4cdde-119">Notes</span><span class="sxs-lookup"><span data-stu-id="4cdde-119">Remarks</span></span>  

 <span data-ttu-id="4cdde-120">L' `add` élément ajoute un module d’authentification à la fin de la liste des modules d’authentification inscrits.</span><span class="sxs-lookup"><span data-stu-id="4cdde-120">The `add` element adds an authentication module to the end of the list of registered authentication modules.</span></span> <span data-ttu-id="4cdde-121">Les modules d’authentification sont appelés dans l’ordre dans lequel ils ont été ajoutés à la liste.</span><span class="sxs-lookup"><span data-stu-id="4cdde-121">Authentication modules are called in the order in which they were added to the list.</span></span>  
  
 <span data-ttu-id="4cdde-122">La valeur de l' `type` attribut doit être un nom de type valide et le nom d’assembly correspondant, séparés par une virgule.</span><span class="sxs-lookup"><span data-stu-id="4cdde-122">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="4cdde-123">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="4cdde-123">Configuration Files</span></span>  

 <span data-ttu-id="4cdde-124">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="4cdde-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4cdde-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="4cdde-125">Example</span></span>  

 <span data-ttu-id="4cdde-126">L’exemple suivant active les modules d’authentification par défaut.</span><span class="sxs-lookup"><span data-stu-id="4cdde-126">The following example enables the default authentication modules.</span></span> <span data-ttu-id="4cdde-127">Vous devez remplacer les valeurs de version et PublicKeyToken par les valeurs correctes pour le module spécifié.</span><span class="sxs-lookup"><span data-stu-id="4cdde-127">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
        <authenticationModules>  
            <add type="System.Net.DigestClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
            <add type="System.Net.NegotiateClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
            <add type="System.Net.KerberosClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
            <add type="System.Net.NtlmClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
            <add type="System.Net.BasicClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
        </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4cdde-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4cdde-128">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="4cdde-129">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="4cdde-129">Network Settings Schema</span></span>](index.md)
