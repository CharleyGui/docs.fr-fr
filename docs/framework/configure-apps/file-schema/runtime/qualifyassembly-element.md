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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153917"
---
# <a name="qualifyassembly-element"></a><span data-ttu-id="ebe09-102">Élément \<qualifyAssembly></span><span class="sxs-lookup"><span data-stu-id="ebe09-102">\<qualifyAssembly> Element</span></span>
<span data-ttu-id="ebe09-103">Spécifie le nom complet de l'assembly qui doit être chargé dynamiquement quand un nom partiel est utilisé.</span><span class="sxs-lookup"><span data-stu-id="ebe09-103">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<qualifyAssembly>**  
  
## <a name="syntax"></a><span data-ttu-id="ebe09-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ebe09-104">Syntax</span></span>  
  
```xml  
      <qualifyAssembly partialName=  
      "PartialAssemblyName"  
                 fullName="FullAssemblyName"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ebe09-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ebe09-105">Attributes and Elements</span></span>  
 <span data-ttu-id="ebe09-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ebe09-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ebe09-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="ebe09-107">Attributes</span></span>  
  
|<span data-ttu-id="ebe09-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="ebe09-108">Attribute</span></span>|<span data-ttu-id="ebe09-109">Description</span><span class="sxs-lookup"><span data-stu-id="ebe09-109">Description</span></span>|  
|---------------|-----------------|  
|`partialName`|<span data-ttu-id="ebe09-110">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="ebe09-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="ebe09-111">Spécifie le nom partiel de l’assembly tel qu’il apparaît dans le code.</span><span class="sxs-lookup"><span data-stu-id="ebe09-111">Specifies the partial name of the assembly as it appears in the code.</span></span>|  
|`fullName`|<span data-ttu-id="ebe09-112">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="ebe09-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="ebe09-113">Spécifie le nom complet de l’assembly tel qu’il apparaît dans la Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="ebe09-113">Specifies the full name of the assembly as it appears in the global assembly cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ebe09-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ebe09-114">Child Elements</span></span>  
 <span data-ttu-id="ebe09-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ebe09-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ebe09-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ebe09-116">Parent Elements</span></span>  
  
|<span data-ttu-id="ebe09-117">Élément</span><span class="sxs-lookup"><span data-stu-id="ebe09-117">Element</span></span>|<span data-ttu-id="ebe09-118">Description</span><span class="sxs-lookup"><span data-stu-id="ebe09-118">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="ebe09-119">Contient des informations à propos de la redirection des versions d'assemblys et de l'emplacement de ces derniers.</span><span class="sxs-lookup"><span data-stu-id="ebe09-119">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="ebe09-120">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ebe09-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="ebe09-121">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="ebe09-121">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ebe09-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="ebe09-122">Remarks</span></span>  
 <span data-ttu-id="ebe09-123">L’appel de la <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> méthode à l’aide de noms d’assemblys partiels amène le Common Language Runtime à Rechercher l’assembly uniquement dans le répertoire de base de l’application.</span><span class="sxs-lookup"><span data-stu-id="ebe09-123">Calling the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method using partial assembly names causes the common language runtime to look for the assembly only in the application base directory.</span></span> <span data-ttu-id="ebe09-124">Utilisez l' **\<qualifyAssembly>** élément dans votre fichier de configuration de l’application pour fournir les informations complètes de l’assembly (nom, version, jeton de clé publique et culture) et faites en sorte que l’Common Language Runtime recherche l’assembly dans le global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="ebe09-124">Use the **\<qualifyAssembly>** element in your application configuration file to provide the full assembly information (name, version, public key token, and culture) and cause the common language runtime to search for the assembly in the global assembly cache.</span></span>  
  
 <span data-ttu-id="ebe09-125">L’attribut **FullName** doit inclure les quatre champs d’identité d’assembly : nom, version, jeton de clé publique et culture.</span><span class="sxs-lookup"><span data-stu-id="ebe09-125">The **fullName** attribute must include the four fields of assembly identity: name, version, public key token, and culture.</span></span> <span data-ttu-id="ebe09-126">L’attribut **partialName** doit référencer partiellement un assembly.</span><span class="sxs-lookup"><span data-stu-id="ebe09-126">The **partialName** attribute must partially reference an assembly.</span></span> <span data-ttu-id="ebe09-127">Vous devez spécifier au moins le nom du texte de l’assembly (le cas le plus courant), mais vous pouvez également inclure la version, le jeton de clé publique ou la culture (ou n’importe quelle combinaison des quatre, mais pas les quatre).</span><span class="sxs-lookup"><span data-stu-id="ebe09-127">You must specify at least the assembly's text name (the most common case), but you can also include version, public key token, or culture (or any combination of the four, but not all four).</span></span> <span data-ttu-id="ebe09-128">L' **partialName** doit correspondre au nom spécifié dans votre appel.</span><span class="sxs-lookup"><span data-stu-id="ebe09-128">The **partialName** must match the name specified in your call.</span></span> <span data-ttu-id="ebe09-129">Par exemple, vous ne pouvez pas spécifier `"math"` comme attribut **partialName** dans votre fichier de configuration et appeler `Assembly.Load("math, Version=3.3.3.3")` dans votre code.</span><span class="sxs-lookup"><span data-stu-id="ebe09-129">For example, you cannot specify `"math"` as the **partialName** attribute in your configuration file and call `Assembly.Load("math, Version=3.3.3.3")` in your code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ebe09-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="ebe09-130">Example</span></span>  
 <span data-ttu-id="ebe09-131">L’exemple suivant transforme logiquement l’appel `Assembly.Load("math")` en `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")` .</span><span class="sxs-lookup"><span data-stu-id="ebe09-131">The following example logically turns the call `Assembly.Load("math")` into `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ebe09-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ebe09-132">See also</span></span>

- [<span data-ttu-id="ebe09-133">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="ebe09-133">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ebe09-134">Méthode de localisation des assemblys par le runtime</span><span class="sxs-lookup"><span data-stu-id="ebe09-134">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
- <span data-ttu-id="ebe09-135">[Références d'assembly partielles](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ebe09-135">[Partial Assembly References](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))</span></span>
