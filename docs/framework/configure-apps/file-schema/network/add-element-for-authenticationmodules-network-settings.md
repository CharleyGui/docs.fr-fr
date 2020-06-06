---
title: <add>, élément d’authenticationModules (paramètres réseau)
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
ms.openlocfilehash: 4181a045079bdb455a63ebda722dd6b0daf33c4d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155113"
---
# <a name="add-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="dd64a-102">\<add>, élément d’authenticationModules (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="dd64a-102">\<add> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="dd64a-103">Ajoute un module d’authentification à l’application.</span><span class="sxs-lookup"><span data-stu-id="dd64a-103">Adds an authentication module to the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="dd64a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dd64a-104">Syntax</span></span>  
  
```xml  
<add
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dd64a-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="dd64a-105">Attributes and Elements</span></span>  
 <span data-ttu-id="dd64a-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="dd64a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dd64a-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="dd64a-107">Attributes</span></span>  
  
|<span data-ttu-id="dd64a-108">**Attribut**</span><span class="sxs-lookup"><span data-stu-id="dd64a-108">**Attribute**</span></span>|<span data-ttu-id="dd64a-109">**Description**</span><span class="sxs-lookup"><span data-stu-id="dd64a-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="dd64a-110">Nom de type qualifié complet (indiqué par la <xref:System.Type.FullName%2A> propriété) et nom de l’assembly (indiqué par la <xref:System.Reflection.Assembly.FullName%2A> propriété), séparés par une virgule.</span><span class="sxs-lookup"><span data-stu-id="dd64a-110">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dd64a-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="dd64a-111">Child Elements</span></span>  
 <span data-ttu-id="dd64a-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="dd64a-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dd64a-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="dd64a-113">Parent Elements</span></span>  
  
|<span data-ttu-id="dd64a-114">**Appartient**</span><span class="sxs-lookup"><span data-stu-id="dd64a-114">**Element**</span></span>|<span data-ttu-id="dd64a-115">**Description**</span><span class="sxs-lookup"><span data-stu-id="dd64a-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="dd64a-116">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="dd64a-116">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="dd64a-117">Spécifie les modules utilisés pour authentifier les demandes réseau.</span><span class="sxs-lookup"><span data-stu-id="dd64a-117">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd64a-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="dd64a-118">Remarks</span></span>  
 <span data-ttu-id="dd64a-119">L' `add` élément ajoute un module d’authentification à la fin de la liste des modules d’authentification inscrits.</span><span class="sxs-lookup"><span data-stu-id="dd64a-119">The `add` element adds an authentication module to the end of the list of registered authentication modules.</span></span> <span data-ttu-id="dd64a-120">Les modules d’authentification sont appelés dans l’ordre dans lequel ils ont été ajoutés à la liste.</span><span class="sxs-lookup"><span data-stu-id="dd64a-120">Authentication modules are called in the order in which they were added to the list.</span></span>  
  
 <span data-ttu-id="dd64a-121">La valeur de l' `type` attribut doit être un nom de type valide et le nom d’assembly correspondant, séparés par une virgule.</span><span class="sxs-lookup"><span data-stu-id="dd64a-121">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="dd64a-122">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="dd64a-122">Configuration Files</span></span>  
 <span data-ttu-id="dd64a-123">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="dd64a-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd64a-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="dd64a-124">Example</span></span>  
 <span data-ttu-id="dd64a-125">L’exemple suivant active les modules d’authentification par défaut.</span><span class="sxs-lookup"><span data-stu-id="dd64a-125">The following example enables the default authentication modules.</span></span> <span data-ttu-id="dd64a-126">Vous devez remplacer les valeurs de version et PublicKeyToken par les valeurs correctes pour le module spécifié.</span><span class="sxs-lookup"><span data-stu-id="dd64a-126">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dd64a-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dd64a-127">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="dd64a-128">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="dd64a-128">Network Settings Schema</span></span>](index.md)
