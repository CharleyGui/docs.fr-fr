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
ms.openlocfilehash: 9c011cf1216b98fa20e330e185e4cf2c331b31d4
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74087953"
---
# <a name="add-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="825b3-102">\<ajouter un élément > pour authenticationModules (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="825b3-102">\<add> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="825b3-103">Ajoute un module d’authentification à l’application.</span><span class="sxs-lookup"><span data-stu-id="825b3-103">Adds an authentication module to the application.</span></span>  

<span data-ttu-id="825b3-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="825b3-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="825b3-105">&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="825b3-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="825b3-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<authenticationModules**](authenticationmodules-element-network-settings.md) ></span><span class="sxs-lookup"><span data-stu-id="825b3-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)</span></span>\
<span data-ttu-id="825b3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**ajouter >**</span><span class="sxs-lookup"><span data-stu-id="825b3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="825b3-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="825b3-108">Syntax</span></span>  
  
```xml  
<add
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="825b3-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="825b3-109">Attributes and Elements</span></span>  
 <span data-ttu-id="825b3-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="825b3-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="825b3-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="825b3-111">Attributes</span></span>  
  
|<span data-ttu-id="825b3-112">**Attribut**</span><span class="sxs-lookup"><span data-stu-id="825b3-112">**Attribute**</span></span>|<span data-ttu-id="825b3-113">**Description**</span><span class="sxs-lookup"><span data-stu-id="825b3-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="825b3-114">Le nom de type qualifié complet (indiqué par la propriété <xref:System.Type.FullName%2A>) et le nom de l’assembly (indiqué par la propriété <xref:System.Reflection.Assembly.FullName%2A>), séparés par une virgule.</span><span class="sxs-lookup"><span data-stu-id="825b3-114">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="825b3-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="825b3-115">Child Elements</span></span>  
 <span data-ttu-id="825b3-116">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="825b3-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="825b3-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="825b3-117">Parent Elements</span></span>  
  
|<span data-ttu-id="825b3-118">**Élément**</span><span class="sxs-lookup"><span data-stu-id="825b3-118">**Element**</span></span>|<span data-ttu-id="825b3-119">**Description**</span><span class="sxs-lookup"><span data-stu-id="825b3-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="825b3-120">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="825b3-120">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="825b3-121">Spécifie les modules utilisés pour authentifier les demandes réseau.</span><span class="sxs-lookup"><span data-stu-id="825b3-121">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="825b3-122">Notes</span><span class="sxs-lookup"><span data-stu-id="825b3-122">Remarks</span></span>  
 <span data-ttu-id="825b3-123">L’élément `add` ajoute un module d’authentification à la fin de la liste des modules d’authentification inscrits.</span><span class="sxs-lookup"><span data-stu-id="825b3-123">The `add` element adds an authentication module to the end of the list of registered authentication modules.</span></span> <span data-ttu-id="825b3-124">Les modules d’authentification sont appelés dans l’ordre dans lequel ils ont été ajoutés à la liste.</span><span class="sxs-lookup"><span data-stu-id="825b3-124">Authentication modules are called in the order in which they were added to the list.</span></span>  
  
 <span data-ttu-id="825b3-125">La valeur de l’attribut `type` doit être un nom de type valide et le nom d’assembly correspondant, séparés par une virgule.</span><span class="sxs-lookup"><span data-stu-id="825b3-125">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="825b3-126">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="825b3-126">Configuration Files</span></span>  
 <span data-ttu-id="825b3-127">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="825b3-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="825b3-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="825b3-128">Example</span></span>  
 <span data-ttu-id="825b3-129">L’exemple suivant active les modules d’authentification par défaut.</span><span class="sxs-lookup"><span data-stu-id="825b3-129">The following example enables the default authentication modules.</span></span> <span data-ttu-id="825b3-130">Vous devez remplacer les valeurs de version et PublicKeyToken par les valeurs correctes pour le module spécifié.</span><span class="sxs-lookup"><span data-stu-id="825b3-130">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="825b3-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="825b3-131">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="825b3-132">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="825b3-132">Network Settings Schema</span></span>](index.md)
