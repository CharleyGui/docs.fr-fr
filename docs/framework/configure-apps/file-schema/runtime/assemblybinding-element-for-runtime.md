---
title: Élément <assemblyBinding> pour <runtime>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding
helpviewer_keywords:
- <assemblyBinding> element
- assemblyBinding element
- container tags, <assemblyBinding> element
ms.assetid: 964cbb35-ab49-4498-8471-209689e5dada
ms.openlocfilehash: 202b063ad3f0f9696cdc12aff434d61fe5a813e6
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154320"
---
# <a name="assemblybinding-element-for-runtime"></a><span data-ttu-id="2461a-102">\<assemblyBinding>, élément de \<runtime></span><span class="sxs-lookup"><span data-stu-id="2461a-102">\<assemblyBinding> Element for \<runtime></span></span>
<span data-ttu-id="2461a-103">Contient des informations à propos de la redirection des versions d'assemblys et de l'emplacement de ces derniers.</span><span class="sxs-lookup"><span data-stu-id="2461a-103">Contains information about assembly version redirection and the locations of assemblies.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<assemblyBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="2461a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2461a-104">Syntax</span></span>  
  
```xml  
      <assemblyBinding
   xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
</assemblyBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2461a-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="2461a-105">Attributes and Elements</span></span>  
 <span data-ttu-id="2461a-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="2461a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2461a-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="2461a-107">Attributes</span></span>  
  
|<span data-ttu-id="2461a-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="2461a-108">Attribute</span></span>|<span data-ttu-id="2461a-109">Description</span><span class="sxs-lookup"><span data-stu-id="2461a-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2461a-110">**xmlns**</span><span class="sxs-lookup"><span data-stu-id="2461a-110">**xmlns**</span></span>|<span data-ttu-id="2461a-111">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="2461a-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="2461a-112">Spécifie l'espace de noms XML requis pour la liaison d'assembly.</span><span class="sxs-lookup"><span data-stu-id="2461a-112">Specifies the XML namespace required for assembly binding.</span></span> <span data-ttu-id="2461a-113">Utilisez la chaîne « urn:schemas-microsoft-com:asm.v1 » comme valeur.</span><span class="sxs-lookup"><span data-stu-id="2461a-113">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span></span>|  
|<span data-ttu-id="2461a-114">**appliesTo**</span><span class="sxs-lookup"><span data-stu-id="2461a-114">**appliesTo**</span></span>|<span data-ttu-id="2461a-115">Spécifie la version du runtime à laquelle s'applique la redirection d'assembly .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2461a-115">Specifies the runtime version the .NET Framework assembly redirection applies to.</span></span> <span data-ttu-id="2461a-116">Cet attribut facultatif utilise un numéro de version .NET Framework pour indiquer la version à laquelle il s'applique.</span><span class="sxs-lookup"><span data-stu-id="2461a-116">This optional attribute uses a .NET Framework version number to indicate what version it applies to.</span></span> <span data-ttu-id="2461a-117">Si aucun attribut **appliesTo** n’est spécifié, l' **\<assemblyBinding>** élément s’applique à toutes les versions du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2461a-117">If no **appliesTo** attribute is specified, the **\<assemblyBinding>** element applies to all versions of the .NET Framework.</span></span> <span data-ttu-id="2461a-118">L’attribut **appliesTo** a été introduit dans .NET Framework version 1,1 ; elle est ignorée par la version de .NET Framework 1,0.</span><span class="sxs-lookup"><span data-stu-id="2461a-118">The **appliesTo** attribute was introduced in .NET Framework version 1.1; it is ignored by the .NET Framework version 1.0.</span></span> <span data-ttu-id="2461a-119">Cela signifie que tous les **\<assemblyBinding>** éléments sont appliqués lors de l’utilisation de la version 1,0 de .NET Framework, même si un attribut **appliesTo** est spécifié.</span><span class="sxs-lookup"><span data-stu-id="2461a-119">This means that all **\<assemblyBinding>** elements are applied when using the .NET Framework version 1.0, even if an **appliesTo** attribute is specified.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2461a-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2461a-120">Child Elements</span></span>  
  
|<span data-ttu-id="2461a-121">Élément</span><span class="sxs-lookup"><span data-stu-id="2461a-121">Element</span></span>|<span data-ttu-id="2461a-122">Description</span><span class="sxs-lookup"><span data-stu-id="2461a-122">Description</span></span>|  
|-------------|-----------------|  
|[\<dependentAssembly>](dependentassembly-element.md)|<span data-ttu-id="2461a-123">Encapsule la stratégie de liaison et l'emplacement d'un assembly.</span><span class="sxs-lookup"><span data-stu-id="2461a-123">Encapsulates binding policy and assembly location for an assembly.</span></span> <span data-ttu-id="2461a-124">Utilisez une **\<dependentAssembly>** balise pour chaque assembly.</span><span class="sxs-lookup"><span data-stu-id="2461a-124">Use one **\<dependentAssembly>** tag for each assembly.</span></span>|  
|[\<probing>](probing-element.md)|<span data-ttu-id="2461a-125">Spécifie les sous-répertoires interrogés par le Common Language Runtime lors du chargement des assemblys.</span><span class="sxs-lookup"><span data-stu-id="2461a-125">Specifies subdirectories the common language runtime searches when loading assemblies.</span></span>|  
|[\<publisherPolicy>](publisherpolicy-element.md)|<span data-ttu-id="2461a-126">Spécifie si le runtime applique la stratégie de l'éditeur.</span><span class="sxs-lookup"><span data-stu-id="2461a-126">Specifies whether the runtime applies publisher policy.</span></span>|  
|[\<qualifyAssembly>](qualifyassembly-element.md)|<span data-ttu-id="2461a-127">Spécifie le nom complet de l'assembly qui doit être chargé dynamiquement quand un nom partiel est utilisé.</span><span class="sxs-lookup"><span data-stu-id="2461a-127">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2461a-128">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2461a-128">Parent Elements</span></span>  
  
|<span data-ttu-id="2461a-129">Élément</span><span class="sxs-lookup"><span data-stu-id="2461a-129">Element</span></span>|<span data-ttu-id="2461a-130">Description</span><span class="sxs-lookup"><span data-stu-id="2461a-130">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="2461a-131">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2461a-131">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="2461a-132">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="2461a-132">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2461a-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="2461a-133">Example</span></span>  
 <span data-ttu-id="2461a-134">L'exemple suivant montre comment rediriger une version d'assembly vers une autre et fournir une base de code.</span><span class="sxs-lookup"><span data-stu-id="2461a-134">The following example shows how to redirect one assembly version to another and provide a codebase.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <bindingRedirect oldVersion="1.0.0.0"  
                             newVersion="2.0.0.0"/>  
            <codeBase version="2.0.0.0"  
                      href="http://www.litwareinc.com/myAssembly.dll"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="2461a-135">L’exemple suivant montre comment utiliser l’attribut **appliesTo** pour rediriger la liaison d’un assembly de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2461a-135">The following example shows how to use the **appliesTo** attribute to redirect binding of a .NET Framework assembly.</span></span>  
  
```xml  
<runtime>  
   <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
      <dependentAssembly>
         <assemblyIdentity name="mscorcfg" publicKeyToken="b03f5f7f11d50a3a" culture=""/>  
         <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="1.0.3300.0"/>  
      </dependentAssembly>  
   </assemblyBinding>  
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2461a-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2461a-136">See also</span></span>

- [<span data-ttu-id="2461a-137">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="2461a-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="2461a-138">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="2461a-138">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="2461a-139">Redirection des versions d'assemblys</span><span class="sxs-lookup"><span data-stu-id="2461a-139">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
