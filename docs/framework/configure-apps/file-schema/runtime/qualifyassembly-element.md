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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 581b19cf74dcb5c2d5c4a549847629503fe0b6ff
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252373"
---
# <a name="qualifyassembly-element"></a><span data-ttu-id="b4e1c-102">\<qualifyAssembly >, élément</span><span class="sxs-lookup"><span data-stu-id="b4e1c-102">\<qualifyAssembly> Element</span></span>
<span data-ttu-id="b4e1c-103">Spécifie le nom complet de l'assembly qui doit être chargé dynamiquement quand un nom partiel est utilisé.</span><span class="sxs-lookup"><span data-stu-id="b4e1c-103">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>  
  
<span data-ttu-id="b4e1c-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b4e1c-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b4e1c-105">&nbsp;&nbsp;[ **\<> d’exécution**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="b4e1c-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="b4e1c-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<assemblyBinding >** ](assemblybinding-element-for-runtime.md)</span><span class="sxs-lookup"><span data-stu-id="b4e1c-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="b4e1c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<qualifyAssembly>**</span><span class="sxs-lookup"><span data-stu-id="b4e1c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<qualifyAssembly>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4e1c-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b4e1c-108">Syntax</span></span>  
  
```xml  
      <qualifyAssembly partialName=  
      "PartialAssemblyName"  
                 fullName="FullAssemblyName"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b4e1c-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b4e1c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b4e1c-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b4e1c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b4e1c-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="b4e1c-111">Attributes</span></span>  
  
|<span data-ttu-id="b4e1c-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="b4e1c-112">Attribute</span></span>|<span data-ttu-id="b4e1c-113">Description</span><span class="sxs-lookup"><span data-stu-id="b4e1c-113">Description</span></span>|  
|---------------|-----------------|  
|`partialName`|<span data-ttu-id="b4e1c-114">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="b4e1c-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="b4e1c-115">Spécifie le nom partiel de l’assembly tel qu’il apparaît dans le code.</span><span class="sxs-lookup"><span data-stu-id="b4e1c-115">Specifies the partial name of the assembly as it appears in the code.</span></span>|  
|`fullName`|<span data-ttu-id="b4e1c-116">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="b4e1c-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="b4e1c-117">Spécifie le nom complet de l’assembly tel qu’il apparaît dans la Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="b4e1c-117">Specifies the full name of the assembly as it appears in the global assembly cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b4e1c-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b4e1c-118">Child Elements</span></span>  
 <span data-ttu-id="b4e1c-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="b4e1c-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b4e1c-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b4e1c-120">Parent Elements</span></span>  
  
|<span data-ttu-id="b4e1c-121">Élément</span><span class="sxs-lookup"><span data-stu-id="b4e1c-121">Element</span></span>|<span data-ttu-id="b4e1c-122">Description</span><span class="sxs-lookup"><span data-stu-id="b4e1c-122">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="b4e1c-123">Contient des informations à propos de la redirection des versions d'assemblys et de l'emplacement de ces derniers.</span><span class="sxs-lookup"><span data-stu-id="b4e1c-123">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="b4e1c-124">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b4e1c-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="b4e1c-125">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="b4e1c-125">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b4e1c-126">Notes</span><span class="sxs-lookup"><span data-stu-id="b4e1c-126">Remarks</span></span>  
 <span data-ttu-id="b4e1c-127">L’appel <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> de la méthode à l’aide de noms d’assemblys partiels amène le Common Language Runtime à Rechercher l’assembly uniquement dans le répertoire de base de l’application.</span><span class="sxs-lookup"><span data-stu-id="b4e1c-127">Calling the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method using partial assembly names causes the common language runtime to look for the assembly only in the application base directory.</span></span> <span data-ttu-id="b4e1c-128">Utilisez l'  **\<élément qualifyAssembly >** de votre fichier de configuration de l’application pour fournir les informations complètes sur l’assembly (nom, version, jeton de clé publique et culture) et faire en sorte que l’Common Language Runtime recherche l’assembly dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="b4e1c-128">Use the **\<qualifyAssembly>** element in your application configuration file to provide the full assembly information (name, version, public key token, and culture) and cause the common language runtime to search for the assembly in the global assembly cache.</span></span>  
  
 <span data-ttu-id="b4e1c-129">L’attribut **FullName** doit inclure les quatre champs d’identité d’assembly : nom, version, jeton de clé publique et culture.</span><span class="sxs-lookup"><span data-stu-id="b4e1c-129">The **fullName** attribute must include the four fields of assembly identity: name, version, public key token, and culture.</span></span> <span data-ttu-id="b4e1c-130">L’attribut **partialName** doit référencer partiellement un assembly.</span><span class="sxs-lookup"><span data-stu-id="b4e1c-130">The **partialName** attribute must partially reference an assembly.</span></span> <span data-ttu-id="b4e1c-131">Vous devez spécifier au moins le nom du texte de l’assembly (le cas le plus courant), mais vous pouvez également inclure la version, le jeton de clé publique ou la culture (ou n’importe quelle combinaison des quatre, mais pas les quatre).</span><span class="sxs-lookup"><span data-stu-id="b4e1c-131">You must specify at least the assembly's text name (the most common case), but you can also include version, public key token, or culture (or any combination of the four, but not all four).</span></span> <span data-ttu-id="b4e1c-132">L' **partialName** doit correspondre au nom spécifié dans votre appel.</span><span class="sxs-lookup"><span data-stu-id="b4e1c-132">The **partialName** must match the name specified in your call.</span></span> <span data-ttu-id="b4e1c-133">Par exemple, vous ne pouvez `"math"` pas spécifier comme attribut **partialName** dans votre fichier de configuration `Assembly.Load("math, Version=3.3.3.3")` et appeler dans votre code.</span><span class="sxs-lookup"><span data-stu-id="b4e1c-133">For example, you cannot specify `"math"` as the **partialName** attribute in your configuration file and call `Assembly.Load("math, Version=3.3.3.3")` in your code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4e1c-134">Exemple</span><span class="sxs-lookup"><span data-stu-id="b4e1c-134">Example</span></span>  
 <span data-ttu-id="b4e1c-135">L’exemple suivant transforme logiquement l' `Assembly.Load("math")` appel `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`en.</span><span class="sxs-lookup"><span data-stu-id="b4e1c-135">The following example logically turns the call `Assembly.Load("math")` into `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b4e1c-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b4e1c-136">See also</span></span>

- [<span data-ttu-id="b4e1c-137">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="b4e1c-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="b4e1c-138">Méthode de localisation des assemblys par le runtime</span><span class="sxs-lookup"><span data-stu-id="b4e1c-138">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
- <span data-ttu-id="b4e1c-139">[Références d’assembly partielles](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b4e1c-139">[Partial Assembly References](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))</span></span>
