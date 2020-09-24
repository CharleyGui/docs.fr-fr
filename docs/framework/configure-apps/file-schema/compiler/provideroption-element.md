---
title: Élément <providerOption>
ms.date: 03/30/2017
f1_keywords:
- provideroption
helpviewer_keywords:
- <provideroption> element
- providerOptions
- provideroption element
ms.assetid: 014f2e0b-c0b5-4fc4-92d3-73f02978b2a1
ms.openlocfilehash: 9374fbaf7ceb61e5b72335417d32a08525477e0d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149632"
---
# <a name="provideroption-element"></a><span data-ttu-id="6713d-102">Élément \<providerOption></span><span class="sxs-lookup"><span data-stu-id="6713d-102">\<providerOption> Element</span></span>

<span data-ttu-id="6713d-103">Spécifie les attributs de version du compilateur pour un fournisseur de langages.</span><span class="sxs-lookup"><span data-stu-id="6713d-103">Specifies the compiler version attributes for a language provider.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<compilers>**](compilers-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<compiler>**](compiler-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<providerOption>**

## <a name="syntax"></a><span data-ttu-id="6713d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6713d-104">Syntax</span></span>  
  
```xml  
<providerOption  
  name="option-name"  
  value="option-value"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6713d-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="6713d-105">Attributes and Elements</span></span>  

 <span data-ttu-id="6713d-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="6713d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6713d-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="6713d-107">Attributes</span></span>  
  
|<span data-ttu-id="6713d-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="6713d-108">Attribute</span></span>|<span data-ttu-id="6713d-109">Description</span><span class="sxs-lookup"><span data-stu-id="6713d-109">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="6713d-110">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="6713d-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="6713d-111">Spécifie le nom de l’option ; par exemple, « CompilerVersion ».</span><span class="sxs-lookup"><span data-stu-id="6713d-111">Specifies the name of the option; for example, "CompilerVersion".</span></span>|  
|`value`|<span data-ttu-id="6713d-112">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="6713d-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="6713d-113">Spécifie la valeur de l’option. par exemple, « v 3.5 ».</span><span class="sxs-lookup"><span data-stu-id="6713d-113">Specifies the value for the option; for example, "v3.5".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6713d-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6713d-114">Child Elements</span></span>  

 <span data-ttu-id="6713d-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="6713d-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6713d-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6713d-116">Parent Elements</span></span>  
  
|<span data-ttu-id="6713d-117">Élément</span><span class="sxs-lookup"><span data-stu-id="6713d-117">Element</span></span>|<span data-ttu-id="6713d-118">Description</span><span class="sxs-lookup"><span data-stu-id="6713d-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6713d-119">\<configuration> Appartient</span><span class="sxs-lookup"><span data-stu-id="6713d-119">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="6713d-120">Élément racine dans chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6713d-120">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="6713d-121">\<system.codedom> Appartient</span><span class="sxs-lookup"><span data-stu-id="6713d-121">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="6713d-122">Spécifie les paramètres de configuration du compilateur pour les fournisseurs de langages disponibles.</span><span class="sxs-lookup"><span data-stu-id="6713d-122">Specifies compiler configuration settings for available language providers.</span></span>|  
|[<span data-ttu-id="6713d-123">\<compilers> Appartient</span><span class="sxs-lookup"><span data-stu-id="6713d-123">\<compilers> Element</span></span>](compilers-element.md)|<span data-ttu-id="6713d-124">Conteneur pour les éléments de configuration du compilateur ; contient zéro ou plusieurs `<compiler>` éléments.</span><span class="sxs-lookup"><span data-stu-id="6713d-124">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|  
|[<span data-ttu-id="6713d-125">\<compiler> Appartient</span><span class="sxs-lookup"><span data-stu-id="6713d-125">\<compiler> Element</span></span>](compiler-element.md)|<span data-ttu-id="6713d-126">Spécifie les attributs de configuration du compilateur pour un fournisseur de langage.</span><span class="sxs-lookup"><span data-stu-id="6713d-126">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6713d-127">Notes</span><span class="sxs-lookup"><span data-stu-id="6713d-127">Remarks</span></span>  

 <span data-ttu-id="6713d-128">Dans la version 3,5, .NET Framework les fournisseurs de code Code Document Object Model (CodeDOM) peuvent prendre en charge des options spécifiques au fournisseur à l’aide de l' `<providerOption>` élément.</span><span class="sxs-lookup"><span data-stu-id="6713d-128">In the .NET Framework version 3.5, Code Document Object Model (CodeDOM) code providers can support provider-specific options by using the `<providerOption>` element.</span></span>  
  
 <span data-ttu-id="6713d-129">Le .NET Framework 3,5 inclut des assemblys .NET Framework 2,0 mis à jour et fournit de nouveaux assemblys de version 3,5 qui contiennent de nouveaux types.</span><span class="sxs-lookup"><span data-stu-id="6713d-129">The .NET Framework 3.5 includes updated .NET Framework 2.0 assemblies and provides new version 3.5 assemblies that contain new types.</span></span> <span data-ttu-id="6713d-130">Les fournisseurs de code Microsoft C# et Visual Basic sont contenus dans les assemblys .NET Framework 2,0, mais ils ont été mis à jour pour prendre en charge les compilateurs de version 3,5.</span><span class="sxs-lookup"><span data-stu-id="6713d-130">The Microsoft C# and Visual Basic code providers are contained in .NET Framework 2.0 assemblies but have been updated to support version 3.5 compilers.</span></span> <span data-ttu-id="6713d-131">Par défaut, les fournisseurs de code mis à jour génèrent du code pour la version 2,0 des compilateurs.</span><span class="sxs-lookup"><span data-stu-id="6713d-131">By default, the updated code providers generate code for version 2.0 compilers.</span></span> <span data-ttu-id="6713d-132">Vous pouvez utiliser l' `<providerOption>` élément pour remplacer la version du compilateur cible par 3,5.</span><span class="sxs-lookup"><span data-stu-id="6713d-132">You can use the `<providerOption>` element to change the target compiler version to 3.5.</span></span> <span data-ttu-id="6713d-133">Pour ce faire, spécifiez « CompilerVersion » pour l' `name` attribut et « v 3.5 » pour l' `value` attribut.</span><span class="sxs-lookup"><span data-stu-id="6713d-133">To do this, specify "CompilerVersion" for the `name` attribute and "v3.5" for the `value` attribute.</span></span> <span data-ttu-id="6713d-134">Vous devez faire précéder le numéro de version d’un « v » en minuscules.</span><span class="sxs-lookup"><span data-stu-id="6713d-134">You must precede the version number with a lower-case "v".</span></span>  
  
 <span data-ttu-id="6713d-135">Vous pouvez rendre la spécification de version globale en ajoutant l' `<providerOption>` élément au fichier .NET Framework 2,0 Machine.config ou racine Web.config.</span><span class="sxs-lookup"><span data-stu-id="6713d-135">You can make the version specification global by adding the `<providerOption>` element to the .NET Framework 2.0 Machine.config or root Web.config file.</span></span> <span data-ttu-id="6713d-136">Si vous mettez à jour la version du compilateur par défaut vers 3,5 dans le fichier Machine.config, vous pouvez la remodifier en 2,0 pour chaque application à l’aide `<providerOption>` de l’élément dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="6713d-136">If you update the default compiler version to 3.5 in the Machine.config file, you can change it back to 2.0 on a per-application basis by using the `<providerOption>` element in the application configuration file.</span></span>  
  
 <span data-ttu-id="6713d-137">Les implémenteurs de fournisseurs de code CodeDOM peuvent traiter des options personnalisées en fournissant un constructeur qui accepte un `providerOptions` paramètre de type <xref:System.Collections.Generic.IDictionary%602> .</span><span class="sxs-lookup"><span data-stu-id="6713d-137">CodeDOM code provider implementers can process custom options by providing a constructor that takes a `providerOptions` parameter of type <xref:System.Collections.Generic.IDictionary%602>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6713d-138">Exemple</span><span class="sxs-lookup"><span data-stu-id="6713d-138">Example</span></span>  

 <span data-ttu-id="6713d-139">L’exemple suivant montre comment spécifier que la version 3,5 du fournisseur de code C# doit être utilisée.</span><span class="sxs-lookup"><span data-stu-id="6713d-139">The following example demonstrates how to specify that version 3.5 of the C# code provider should be used.</span></span>  
  
```xml  
<configuration>  
  <system.codedom>  
    <compilers>  
      <!-- zero or more compiler elements -->  
      <compiler  
        language="c#;cs;csharp"  
        extension=".cs"  
        type="Microsoft.CSharp.CSharpCodeProvider, System,
          Version=2.0.3600.0, Culture=neutral,
          PublicKeyToken=b77a5c561934e089"  
        compilerOptions="/optimize"  
        warningLevel="1" >  
          <providerOption  
            name="CompilerVersion"  
            value="v3.5" />  
      </compiler>  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6713d-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6713d-140">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="6713d-141">Schéma du fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="6713d-141">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="6713d-142">\<compilers> Appartient</span><span class="sxs-lookup"><span data-stu-id="6713d-142">\<compilers> Element</span></span>](compilers-element.md)
- [<span data-ttu-id="6713d-143">Spécification des noms de types qualifiés complets</span><span class="sxs-lookup"><span data-stu-id="6713d-143">Specifying Fully Qualified Type Names</span></span>](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- <span data-ttu-id="6713d-144">[compiler, élément de compilers pour compilation (Schéma des paramètres ASP.NET)](/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="6713d-144">[compiler Element for compilers for compilation (ASP.NET Settings Schema)](/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span></span>
