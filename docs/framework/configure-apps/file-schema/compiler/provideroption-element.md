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
ms.openlocfilehash: a6718173e84ecffc4ba0641f6e865e777aa6b1a4
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088674"
---
# <a name="provideroption-element"></a><span data-ttu-id="19fd6-102">\<élément providerOption ></span><span class="sxs-lookup"><span data-stu-id="19fd6-102">\<providerOption> Element</span></span>
<span data-ttu-id="19fd6-103">Spécifie les attributs de version du compilateur pour un fournisseur de langages.</span><span class="sxs-lookup"><span data-stu-id="19fd6-103">Specifies the compiler version attributes for a language provider.</span></span>  

<span data-ttu-id="19fd6-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="19fd6-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="19fd6-105">&nbsp;&nbsp;[ **\<> System. codedom**](system-codedom-element.md)</span><span class="sxs-lookup"><span data-stu-id="19fd6-105">&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)</span></span>\
<span data-ttu-id="19fd6-106">&nbsp;&nbsp;&nbsp;&nbsp;[**compilateurs**](compilers-element.md)\<</span><span class="sxs-lookup"><span data-stu-id="19fd6-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<compilers>**](compilers-element.md)\</span></span>
<span data-ttu-id="19fd6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**du compilateur**](compiler-element.md) ></span><span class="sxs-lookup"><span data-stu-id="19fd6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<compiler>**](compiler-element.md)\</span></span>
<span data-ttu-id="19fd6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<providerOption >**</span><span class="sxs-lookup"><span data-stu-id="19fd6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<providerOption>**</span></span>

## <a name="syntax"></a><span data-ttu-id="19fd6-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="19fd6-109">Syntax</span></span>  
  
```xml  
<providerOption  
  name="option-name"  
  value="option-value"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="19fd6-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="19fd6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="19fd6-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="19fd6-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="19fd6-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="19fd6-112">Attributes</span></span>  
  
|<span data-ttu-id="19fd6-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="19fd6-113">Attribute</span></span>|<span data-ttu-id="19fd6-114">Description</span><span class="sxs-lookup"><span data-stu-id="19fd6-114">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="19fd6-115">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="19fd6-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="19fd6-116">Spécifie le nom de l’option ; par exemple, « CompilerVersion ».</span><span class="sxs-lookup"><span data-stu-id="19fd6-116">Specifies the name of the option; for example, "CompilerVersion".</span></span>|  
|`value`|<span data-ttu-id="19fd6-117">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="19fd6-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="19fd6-118">Spécifie la valeur de l’option. par exemple, « v 3.5 ».</span><span class="sxs-lookup"><span data-stu-id="19fd6-118">Specifies the value for the option; for example, "v3.5".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="19fd6-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="19fd6-119">Child Elements</span></span>  
 <span data-ttu-id="19fd6-120">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="19fd6-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="19fd6-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="19fd6-121">Parent Elements</span></span>  
  
|<span data-ttu-id="19fd6-122">Élément</span><span class="sxs-lookup"><span data-stu-id="19fd6-122">Element</span></span>|<span data-ttu-id="19fd6-123">Description</span><span class="sxs-lookup"><span data-stu-id="19fd6-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="19fd6-124">\<configuration>, élément</span><span class="sxs-lookup"><span data-stu-id="19fd6-124">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="19fd6-125">Élément racine dans chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="19fd6-125">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="19fd6-126">\<l’élément System. CodeDom ></span><span class="sxs-lookup"><span data-stu-id="19fd6-126">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="19fd6-127">Spécifie les paramètres de configuration du compilateur pour les fournisseurs de langages disponibles.</span><span class="sxs-lookup"><span data-stu-id="19fd6-127">Specifies compiler configuration settings for available language providers.</span></span>|  
|[<span data-ttu-id="19fd6-128">\<les compilateurs > élément</span><span class="sxs-lookup"><span data-stu-id="19fd6-128">\<compilers> Element</span></span>](compilers-element.md)|<span data-ttu-id="19fd6-129">Conteneur pour les éléments de configuration du compilateur ; contient zéro ou plusieurs éléments `<compiler>`.</span><span class="sxs-lookup"><span data-stu-id="19fd6-129">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|  
|[<span data-ttu-id="19fd6-130">\<compiler> Element</span><span class="sxs-lookup"><span data-stu-id="19fd6-130">\<compiler> Element</span></span>](compiler-element.md)|<span data-ttu-id="19fd6-131">Spécifie les attributs de configuration du compilateur pour un fournisseur de langage.</span><span class="sxs-lookup"><span data-stu-id="19fd6-131">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19fd6-132">Notes</span><span class="sxs-lookup"><span data-stu-id="19fd6-132">Remarks</span></span>  
 <span data-ttu-id="19fd6-133">Dans la version 3,5, .NET Framework les fournisseurs de code Code Document Object Model (CodeDOM) peuvent prendre en charge des options spécifiques au fournisseur à l’aide de l’élément `<providerOption>`.</span><span class="sxs-lookup"><span data-stu-id="19fd6-133">In the .NET Framework version 3.5, Code Document Object Model (CodeDOM) code providers can support provider-specific options by using the `<providerOption>` element.</span></span>  
  
 <span data-ttu-id="19fd6-134">Le .NET Framework 3,5 inclut des assemblys .NET Framework 2,0 mis à jour et fournit de nouveaux assemblys de version 3,5 qui contiennent de nouveaux types.</span><span class="sxs-lookup"><span data-stu-id="19fd6-134">The .NET Framework 3.5 includes updated .NET Framework 2.0 assemblies and provides new version 3.5 assemblies that contain new types.</span></span> <span data-ttu-id="19fd6-135">Les fournisseurs C# de code Microsoft et Visual Basic sont contenus dans les assemblys .NET Framework 2,0, mais ils ont été mis à jour pour prendre en charge les compilateurs de version 3,5.</span><span class="sxs-lookup"><span data-stu-id="19fd6-135">The Microsoft C# and Visual Basic code providers are contained in .NET Framework 2.0 assemblies but have been updated to support version 3.5 compilers.</span></span> <span data-ttu-id="19fd6-136">Par défaut, les fournisseurs de code mis à jour génèrent du code pour la version 2,0 des compilateurs.</span><span class="sxs-lookup"><span data-stu-id="19fd6-136">By default, the updated code providers generate code for version 2.0 compilers.</span></span> <span data-ttu-id="19fd6-137">Vous pouvez utiliser l’élément `<providerOption>` pour remplacer la version du compilateur cible par 3,5.</span><span class="sxs-lookup"><span data-stu-id="19fd6-137">You can use the `<providerOption>` element to change the target compiler version to 3.5.</span></span> <span data-ttu-id="19fd6-138">Pour ce faire, spécifiez « CompilerVersion » pour l’attribut `name` et « v 3.5 » pour l’attribut `value`.</span><span class="sxs-lookup"><span data-stu-id="19fd6-138">To do this, specify "CompilerVersion" for the `name` attribute and "v3.5" for the `value` attribute.</span></span> <span data-ttu-id="19fd6-139">Vous devez faire précéder le numéro de version d’un « v » en minuscules.</span><span class="sxs-lookup"><span data-stu-id="19fd6-139">You must precede the version number with a lower-case "v".</span></span>  
  
 <span data-ttu-id="19fd6-140">Vous pouvez rendre la spécification de version globale en ajoutant l’élément `<providerOption>` au fichier. config ou Web. config .NET Framework 2,0 machine. config.</span><span class="sxs-lookup"><span data-stu-id="19fd6-140">You can make the version specification global by adding the `<providerOption>` element to the .NET Framework 2.0 Machine.config or root Web.config file.</span></span> <span data-ttu-id="19fd6-141">Si vous mettez à jour la version du compilateur par défaut à 3,5 dans le fichier machine. config, vous pouvez la remodifier en 2,0 pour chaque application à l’aide de l’élément `<providerOption>` dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="19fd6-141">If you update the default compiler version to 3.5 in the Machine.config file, you can change it back to 2.0 on a per-application basis by using the `<providerOption>` element in the application configuration file.</span></span>  
  
 <span data-ttu-id="19fd6-142">Les implémenteurs de fournisseurs de code CodeDOM peuvent traiter des options personnalisées en fournissant un constructeur qui accepte un paramètre `providerOptions` de type <xref:System.Collections.Generic.IDictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="19fd6-142">CodeDOM code provider implementers can process custom options by providing a constructor that takes a `providerOptions` parameter of type <xref:System.Collections.Generic.IDictionary%602>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="19fd6-143">Exemple</span><span class="sxs-lookup"><span data-stu-id="19fd6-143">Example</span></span>  
 <span data-ttu-id="19fd6-144">L’exemple suivant montre comment spécifier que la C# version 3,5 du fournisseur de code doit être utilisée.</span><span class="sxs-lookup"><span data-stu-id="19fd6-144">The following example demonstrates how to specify that version 3.5 of the C# code provider should be used.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="19fd6-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="19fd6-145">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="19fd6-146">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="19fd6-146">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="19fd6-147">\<les compilateurs > élément</span><span class="sxs-lookup"><span data-stu-id="19fd6-147">\<compilers> Element</span></span>](compilers-element.md)
- [<span data-ttu-id="19fd6-148">Spécification des noms de types complets</span><span class="sxs-lookup"><span data-stu-id="19fd6-148">Specifying Fully Qualified Type Names</span></span>](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- <span data-ttu-id="19fd6-149">[compiler, élément de compilateurs pour compilation (schéma des paramètres ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="19fd6-149">[compiler Element for compilers for compilation (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span></span>
