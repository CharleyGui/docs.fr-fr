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
ms.openlocfilehash: c8ba5b9a0680f5e5102c13eb5bb0c1904a168c07
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155399"
---
# <a name="provideroption-element"></a><span data-ttu-id="db354-102">\<fournisseurOption> Element</span><span class="sxs-lookup"><span data-stu-id="db354-102">\<providerOption> Element</span></span>
<span data-ttu-id="db354-103">Spécifie les attributs de la version compilateur pour un fournisseur de langue.</span><span class="sxs-lookup"><span data-stu-id="db354-103">Specifies the compiler version attributes for a language provider.</span></span>  

<span data-ttu-id="db354-104">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="db354-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="db354-105">&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)</span><span class="sxs-lookup"><span data-stu-id="db354-105">&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)</span></span>\
<span data-ttu-id="db354-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<compilateurs>**](compilers-element.md)</span><span class="sxs-lookup"><span data-stu-id="db354-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<compilers>**](compilers-element.md)</span></span>\
<span data-ttu-id="db354-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<compilateur>**](compiler-element.md)</span><span class="sxs-lookup"><span data-stu-id="db354-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<compiler>**](compiler-element.md)</span></span>\
<span data-ttu-id="db354-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<fournisseurOption>**</span><span class="sxs-lookup"><span data-stu-id="db354-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<providerOption>**</span></span>

## <a name="syntax"></a><span data-ttu-id="db354-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db354-109">Syntax</span></span>  
  
```xml  
<providerOption  
  name="option-name"  
  value="option-value"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="db354-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="db354-110">Attributes and Elements</span></span>  
 <span data-ttu-id="db354-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="db354-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="db354-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="db354-112">Attributes</span></span>  
  
|<span data-ttu-id="db354-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="db354-113">Attribute</span></span>|<span data-ttu-id="db354-114">Description</span><span class="sxs-lookup"><span data-stu-id="db354-114">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="db354-115">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="db354-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="db354-116">Précise le nom de l’option; par exemple, "CompilerVersion".</span><span class="sxs-lookup"><span data-stu-id="db354-116">Specifies the name of the option; for example, "CompilerVersion".</span></span>|  
|`value`|<span data-ttu-id="db354-117">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="db354-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="db354-118">Spécifie la valeur de l’option; par exemple, "v3.5".</span><span class="sxs-lookup"><span data-stu-id="db354-118">Specifies the value for the option; for example, "v3.5".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="db354-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="db354-119">Child Elements</span></span>  
 <span data-ttu-id="db354-120">Aucun.</span><span class="sxs-lookup"><span data-stu-id="db354-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="db354-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="db354-121">Parent Elements</span></span>  
  
|<span data-ttu-id="db354-122">Élément</span><span class="sxs-lookup"><span data-stu-id="db354-122">Element</span></span>|<span data-ttu-id="db354-123">Description</span><span class="sxs-lookup"><span data-stu-id="db354-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="db354-124">\<configuration> Element</span><span class="sxs-lookup"><span data-stu-id="db354-124">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="db354-125">Élément racine dans chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="db354-125">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="db354-126">\<system.codedom> Element</span><span class="sxs-lookup"><span data-stu-id="db354-126">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="db354-127">Spécifie les paramètres de configuration du compilateur pour les fournisseurs de langages disponibles.</span><span class="sxs-lookup"><span data-stu-id="db354-127">Specifies compiler configuration settings for available language providers.</span></span>|  
|[<span data-ttu-id="db354-128">\<compilateurs> Element</span><span class="sxs-lookup"><span data-stu-id="db354-128">\<compilers> Element</span></span>](compilers-element.md)|<span data-ttu-id="db354-129">Conteneur pour éléments de configuration de compilateur; contient zéro `<compiler>` ou plus d’éléments.</span><span class="sxs-lookup"><span data-stu-id="db354-129">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|  
|[<span data-ttu-id="db354-130">\<compilateur> Element</span><span class="sxs-lookup"><span data-stu-id="db354-130">\<compiler> Element</span></span>](compiler-element.md)|<span data-ttu-id="db354-131">Spécifie les attributs de configuration du compilateur pour un fournisseur de langage.</span><span class="sxs-lookup"><span data-stu-id="db354-131">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db354-132">Notes </span><span class="sxs-lookup"><span data-stu-id="db354-132">Remarks</span></span>  
 <span data-ttu-id="db354-133">Dans la version cadre .NET 3.5, les fournisseurs de code Code Document Object `<providerOption>` Model (CodeDOM) peuvent prendre en charge les options spécifiques au fournisseur en utilisant l’élément.</span><span class="sxs-lookup"><span data-stu-id="db354-133">In the .NET Framework version 3.5, Code Document Object Model (CodeDOM) code providers can support provider-specific options by using the `<providerOption>` element.</span></span>  
  
 <span data-ttu-id="db354-134">Le cadre .NET 3.5 comprend des assemblages .NET Framework 2.0 mis à jour et fournit de nouvelles versions 3.5 assemblages qui contiennent de nouveaux types.</span><span class="sxs-lookup"><span data-stu-id="db354-134">The .NET Framework 3.5 includes updated .NET Framework 2.0 assemblies and provides new version 3.5 assemblies that contain new types.</span></span> <span data-ttu-id="db354-135">Les fournisseurs de code Microsoft C et Visual Basic sont contenus dans les assemblages .NET Framework 2.0, mais ont été mis à jour pour prendre en charge les compilateurs de la version 3.5.</span><span class="sxs-lookup"><span data-stu-id="db354-135">The Microsoft C# and Visual Basic code providers are contained in .NET Framework 2.0 assemblies but have been updated to support version 3.5 compilers.</span></span> <span data-ttu-id="db354-136">Par défaut, les fournisseurs de code mis à jour génèrent du code pour les compilateurs de la version 2.0.</span><span class="sxs-lookup"><span data-stu-id="db354-136">By default, the updated code providers generate code for version 2.0 compilers.</span></span> <span data-ttu-id="db354-137">Vous pouvez `<providerOption>` utiliser l’élément pour modifier la version compilateur cible à 3,5.</span><span class="sxs-lookup"><span data-stu-id="db354-137">You can use the `<providerOption>` element to change the target compiler version to 3.5.</span></span> <span data-ttu-id="db354-138">Pour ce faire, spécifiez `name` "CompilerVersion" pour l’attribut et "v3.5" pour l’attribut. `value`</span><span class="sxs-lookup"><span data-stu-id="db354-138">To do this, specify "CompilerVersion" for the `name` attribute and "v3.5" for the `value` attribute.</span></span> <span data-ttu-id="db354-139">Vous devez précéder le numéro de version avec un "v" minuscule.</span><span class="sxs-lookup"><span data-stu-id="db354-139">You must precede the version number with a lower-case "v".</span></span>  
  
 <span data-ttu-id="db354-140">Vous pouvez rendre la spécification de `<providerOption>` la version globale en ajoutant l’élément au fichier .NET Framework 2.0 Machine.config ou Root Web.config.</span><span class="sxs-lookup"><span data-stu-id="db354-140">You can make the version specification global by adding the `<providerOption>` element to the .NET Framework 2.0 Machine.config or root Web.config file.</span></span> <span data-ttu-id="db354-141">Si vous mettez à jour la version compilateur par défaut à 3,5 dans le fichier Machine.config, vous `<providerOption>` pouvez la revenons à 2,0 sur une base par application en utilisant l’élément dans le fichier de configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="db354-141">If you update the default compiler version to 3.5 in the Machine.config file, you can change it back to 2.0 on a per-application basis by using the `<providerOption>` element in the application configuration file.</span></span>  
  
 <span data-ttu-id="db354-142">CodeDOM codeD code provider implementers peut traiter les `providerOptions` options <xref:System.Collections.Generic.IDictionary%602>personnalisées en fournissant un constructeur qui prend un paramètre de type .</span><span class="sxs-lookup"><span data-stu-id="db354-142">CodeDOM code provider implementers can process custom options by providing a constructor that takes a `providerOptions` parameter of type <xref:System.Collections.Generic.IDictionary%602>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db354-143"> Exemple</span><span class="sxs-lookup"><span data-stu-id="db354-143">Example</span></span>  
 <span data-ttu-id="db354-144">L’exemple suivant montre comment spécifier la version 3.5 du fournisseur de code CMD doit être utilisée.</span><span class="sxs-lookup"><span data-stu-id="db354-144">The following example demonstrates how to specify that version 3.5 of the C# code provider should be used.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="db354-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="db354-145">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="db354-146">Configuration Fichier Schema</span><span class="sxs-lookup"><span data-stu-id="db354-146">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="db354-147">\<compilateurs> Element</span><span class="sxs-lookup"><span data-stu-id="db354-147">\<compilers> Element</span></span>](compilers-element.md)
- [<span data-ttu-id="db354-148">Spécification des noms de types qualifiés complets</span><span class="sxs-lookup"><span data-stu-id="db354-148">Specifying Fully Qualified Type Names</span></span>](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- <span data-ttu-id="db354-149">[compiler, élément de compilers pour compilation (Schéma des paramètres ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="db354-149">[compiler Element for compilers for compilation (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span></span>
