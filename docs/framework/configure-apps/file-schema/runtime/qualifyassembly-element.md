---
title: Élément <qualifyAssembly>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#qualifyAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/qualifyAssembly
helpviewer_keywords:
- container tags, <qualifyAssembly> element
- <qualifyAssembly> element
- qualifyAssembly element
ms.assetid: ad6442f6-1a9d-43b6-b733-04ac1b7f9b82
ms.openlocfilehash: 74e83900c68ab4b3fe01beb3f97657b0140d78ad
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153917"
---
# <a name="qualifyassembly-element"></a><span data-ttu-id="e3b4a-102">\<qualifierAssembly> Element</span><span class="sxs-lookup"><span data-stu-id="e3b4a-102">\<qualifyAssembly> Element</span></span>
<span data-ttu-id="e3b4a-103">Spécifie le nom complet de l'assembly qui doit être chargé dynamiquement quand un nom partiel est utilisé.</span><span class="sxs-lookup"><span data-stu-id="e3b4a-103">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>  
  
<span data-ttu-id="e3b4a-104">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e3b4a-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e3b4a-105">&nbsp;&nbsp;[**\<>de temps d’exécution**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="e3b4a-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="e3b4a-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblageBinding>**](assemblybinding-element-for-runtime.md)</span><span class="sxs-lookup"><span data-stu-id="e3b4a-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="e3b4a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<qualifierAssembly>**</span><span class="sxs-lookup"><span data-stu-id="e3b4a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<qualifyAssembly>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3b4a-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e3b4a-108">Syntax</span></span>  
  
```xml  
      <qualifyAssembly partialName=  
      "PartialAssemblyName"  
                 fullName="FullAssemblyName"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e3b4a-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e3b4a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e3b4a-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e3b4a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e3b4a-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="e3b4a-111">Attributes</span></span>  
  
|<span data-ttu-id="e3b4a-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="e3b4a-112">Attribute</span></span>|<span data-ttu-id="e3b4a-113">Description</span><span class="sxs-lookup"><span data-stu-id="e3b4a-113">Description</span></span>|  
|---------------|-----------------|  
|`partialName`|<span data-ttu-id="e3b4a-114">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="e3b4a-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="e3b4a-115">Spécifie le nom partiel de l’assemblage tel qu’il apparaît dans le code.</span><span class="sxs-lookup"><span data-stu-id="e3b4a-115">Specifies the partial name of the assembly as it appears in the code.</span></span>|  
|`fullName`|<span data-ttu-id="e3b4a-116">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="e3b4a-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="e3b4a-117">Spécifie le nom complet de l’assemblée tel qu’il apparaît dans le cache d’assemblage global.</span><span class="sxs-lookup"><span data-stu-id="e3b4a-117">Specifies the full name of the assembly as it appears in the global assembly cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e3b4a-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e3b4a-118">Child Elements</span></span>  
 <span data-ttu-id="e3b4a-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e3b4a-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e3b4a-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e3b4a-120">Parent Elements</span></span>  
  
|<span data-ttu-id="e3b4a-121">Élément</span><span class="sxs-lookup"><span data-stu-id="e3b4a-121">Element</span></span>|<span data-ttu-id="e3b4a-122">Description</span><span class="sxs-lookup"><span data-stu-id="e3b4a-122">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="e3b4a-123">Contient des informations à propos de la redirection des versions d'assemblys et de l'emplacement de ces derniers.</span><span class="sxs-lookup"><span data-stu-id="e3b4a-123">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="e3b4a-124">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e3b4a-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="e3b4a-125">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="e3b4a-125">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3b4a-126">Notes </span><span class="sxs-lookup"><span data-stu-id="e3b4a-126">Remarks</span></span>  
 <span data-ttu-id="e3b4a-127">Appeler <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> la méthode en utilisant des noms d’assemblage partiel provoque le temps de course de langue commune de rechercher l’assemblage seulement dans l’annuaire de base d’application.</span><span class="sxs-lookup"><span data-stu-id="e3b4a-127">Calling the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method using partial assembly names causes the common language runtime to look for the assembly only in the application base directory.</span></span> <span data-ttu-id="e3b4a-128">Utilisez \*\* \<l’élément qualifieAssembly>\*\* dans votre fichier de configuration d’application pour fournir les informations d’assemblage complète (nom, version, jeton de clé publique et culture) et provoquer l’heure d’exécution de la langue commune à rechercher l’assemblage dans le cache d’assemblage global.</span><span class="sxs-lookup"><span data-stu-id="e3b4a-128">Use the **\<qualifyAssembly>** element in your application configuration file to provide the full assembly information (name, version, public key token, and culture) and cause the common language runtime to search for the assembly in the global assembly cache.</span></span>  
  
 <span data-ttu-id="e3b4a-129">**L’attribut FullName** doit inclure les quatre domaines de l’identité de l’assemblage : nom, version, jeton de clé publique et culture.</span><span class="sxs-lookup"><span data-stu-id="e3b4a-129">The **fullName** attribute must include the four fields of assembly identity: name, version, public key token, and culture.</span></span> <span data-ttu-id="e3b4a-130">**L’attribut partielnamise** doit en partie faire référence à une assemblée.</span><span class="sxs-lookup"><span data-stu-id="e3b4a-130">The **partialName** attribute must partially reference an assembly.</span></span> <span data-ttu-id="e3b4a-131">Vous devez spécifier au moins le nom de texte de l’assemblée (le cas le plus courant), mais vous pouvez également inclure la version, le jeton de clé publique, ou la culture (ou toute combinaison des quatre, mais pas les quatre).</span><span class="sxs-lookup"><span data-stu-id="e3b4a-131">You must specify at least the assembly's text name (the most common case), but you can also include version, public key token, or culture (or any combination of the four, but not all four).</span></span> <span data-ttu-id="e3b4a-132">Le **nom partiel** doit correspondre au nom spécifié dans votre appel.</span><span class="sxs-lookup"><span data-stu-id="e3b4a-132">The **partialName** must match the name specified in your call.</span></span> <span data-ttu-id="e3b4a-133">Par exemple, vous `"math"` ne pouvez pas spécifier `Assembly.Load("math, Version=3.3.3.3")` comme attribut **partielName** dans votre fichier de configuration et appeler dans votre code.</span><span class="sxs-lookup"><span data-stu-id="e3b4a-133">For example, you cannot specify `"math"` as the **partialName** attribute in your configuration file and call `Assembly.Load("math, Version=3.3.3.3")` in your code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3b4a-134"> Exemple</span><span class="sxs-lookup"><span data-stu-id="e3b4a-134">Example</span></span>  
 <span data-ttu-id="e3b4a-135">L’exemple suivant transforme `Assembly.Load("math")` logiquement l’appel en `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.</span><span class="sxs-lookup"><span data-stu-id="e3b4a-135">The following example logically turns the call `Assembly.Load("math")` into `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <qualifyAssembly partialName="math"
                         fullName=  
"math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e3b4a-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e3b4a-136">See also</span></span>

- [<span data-ttu-id="e3b4a-137">Schéma des paramètres d'exécution</span><span class="sxs-lookup"><span data-stu-id="e3b4a-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e3b4a-138">Méthode de localisation des assemblys par le runtime</span><span class="sxs-lookup"><span data-stu-id="e3b4a-138">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
- <span data-ttu-id="e3b4a-139">[Références d'assembly partielles](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e3b4a-139">[Partial Assembly References](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))</span></span>
