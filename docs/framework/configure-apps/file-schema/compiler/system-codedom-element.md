---
title: <system.codedom>, élément
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.codedom
helpviewer_keywords:
- compiler configuration elements, <system.codedom> element
- system.codedom element
- <system.codedom> element
ms.assetid: 672a68f7-e69f-4479-ac30-e980085ec4fe
ms.openlocfilehash: 40a3c84e1deed4d215383670176623a6a79ac41d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155386"
---
# <a name="systemcodedom-element"></a><span data-ttu-id="adc6a-102">Élément \<system.codedom></span><span class="sxs-lookup"><span data-stu-id="adc6a-102">\<system.codedom> Element</span></span>
<span data-ttu-id="adc6a-103">Spécifie les paramètres de configuration du compilateur pour les fournisseurs de langages disponibles.</span><span class="sxs-lookup"><span data-stu-id="adc6a-103">Specifies compiler configuration settings for available language providers.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.codedom>**  
  
## <a name="syntax"></a><span data-ttu-id="adc6a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="adc6a-104">Syntax</span></span>  
  
```xml  
<system.codedom>  
  <compilers> ... </compilers>  
</system.codedom>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="adc6a-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="adc6a-105">Attributes and Elements</span></span>  
 <span data-ttu-id="adc6a-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="adc6a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="adc6a-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="adc6a-107">Attributes</span></span>  
 <span data-ttu-id="adc6a-108">Aucun.</span><span class="sxs-lookup"><span data-stu-id="adc6a-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="adc6a-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="adc6a-109">Child Elements</span></span>  
  
|<span data-ttu-id="adc6a-110">Élément</span><span class="sxs-lookup"><span data-stu-id="adc6a-110">Element</span></span>|<span data-ttu-id="adc6a-111">Description</span><span class="sxs-lookup"><span data-stu-id="adc6a-111">Description</span></span>|  
|-------------|-----------------|  
|[\<compilers>](compilers-element.md)|<span data-ttu-id="adc6a-112">Conteneur pour les éléments de configuration du compilateur ; contient zéro ou plusieurs [\<compiler>](compiler-element.md) éléments.</span><span class="sxs-lookup"><span data-stu-id="adc6a-112">Container for compiler configuration elements; contains zero or more [\<compiler>](compiler-element.md) elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="adc6a-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="adc6a-113">Parent Elements</span></span>  
  
|<span data-ttu-id="adc6a-114">Élément</span><span class="sxs-lookup"><span data-stu-id="adc6a-114">Element</span></span>|<span data-ttu-id="adc6a-115">Description</span><span class="sxs-lookup"><span data-stu-id="adc6a-115">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="adc6a-116">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="adc6a-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="adc6a-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="adc6a-117">Remarks</span></span>  
  
## <a name="net-framework-version-20"></a><span data-ttu-id="adc6a-118">.NET Framework version 2,0</span><span class="sxs-lookup"><span data-stu-id="adc6a-118">.NET Framework Version 2.0</span></span>  
 <span data-ttu-id="adc6a-119">L' [\<system.codedom>](system-codedom-element.md) élément contient des paramètres de configuration du compilateur pour les fournisseurs de langages installés sur un ordinateur en plus des fournisseurs par défaut installés avec le .NET Framework, tels que <xref:Microsoft.CSharp.CSharpCodeProvider> et <xref:Microsoft.VisualBasic.VBCodeProvider> .</span><span class="sxs-lookup"><span data-stu-id="adc6a-119">The [\<system.codedom>](system-codedom-element.md) element contains compiler configuration settings for language providers installed on a computer in addition to the default providers that are installed with the .NET Framework, such as the <xref:Microsoft.CSharp.CSharpCodeProvider> and the <xref:Microsoft.VisualBasic.VBCodeProvider>.</span></span> <span data-ttu-id="adc6a-120">L' [\<compilers>](compilers-element.md) élément contient zéro ou plusieurs [\<compiler>](compiler-element.md) éléments.</span><span class="sxs-lookup"><span data-stu-id="adc6a-120">The [\<compilers>](compilers-element.md) element contains zero or more [\<compiler>](compiler-element.md) elements.</span></span> <span data-ttu-id="adc6a-121">Chaque [\<compiler>](compiler-element.md) élément spécifie les attributs de configuration du compilateur pour un fournisseur de langages spécifique.</span><span class="sxs-lookup"><span data-stu-id="adc6a-121">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="adc6a-122">Les développeurs et les fournisseurs de compilateur peuvent ajouter des paramètres de configuration au fichier de configuration de l’ordinateur (machine. config) pour une nouvelle <xref:System.CodeDom.Compiler.CodeDomProvider> implémentation.</span><span class="sxs-lookup"><span data-stu-id="adc6a-122">Developers and compiler vendors can add configuration settings to the machine configuration file (Machine.config) for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="adc6a-123">Utilisez la <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> méthode pour énumérer par programme les fournisseurs de langages par défaut et les fournisseurs de langages identifiés par les paramètres de configuration du compilateur sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="adc6a-123">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate both the default language providers and language providers identified by the compiler configuration settings on a computer.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="adc6a-124">Dans les versions 1,0 et 1,1 du .NET Framework, les fournisseurs de langages par défaut fournis par le .NET Framework sont identifiés dans l' [\<compilers>](compilers-element.md) élément.</span><span class="sxs-lookup"><span data-stu-id="adc6a-124">In the .NET Framework versions 1.0 and 1.1, the default language providers supplied by the .NET Framework are identified in the [\<compilers>](compilers-element.md) element.</span></span> <span data-ttu-id="adc6a-125">Dans la .NET Framework version 2,0, les fournisseurs de langage par défaut ne sont pas identifiés dans l' [\<compilers>](compilers-element.md) élément, mais peuvent être énumérés à l’aide de la <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="adc6a-125">In the .NET Framework version 2.0, the default language providers are not identified in the [\<compilers>](compilers-element.md) element, but can be enumerated using the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> method.</span></span>  
  
## <a name="net-framework-versions-10-and-11"></a><span data-ttu-id="adc6a-126">.NET Framework les versions 1,0 et 1,1</span><span class="sxs-lookup"><span data-stu-id="adc6a-126">.NET Framework Versions 1.0 and 1.1</span></span>  
 <span data-ttu-id="adc6a-127">L' [\<system.codedom>](system-codedom-element.md) élément contient les paramètres de configuration du compilateur pour les fournisseurs de langages sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="adc6a-127">The [\<system.codedom>](system-codedom-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="adc6a-128">L' [\<compilers>](compilers-element.md) élément contient zéro ou plusieurs [\<compiler>](compiler-element.md) éléments.</span><span class="sxs-lookup"><span data-stu-id="adc6a-128">The [\<compilers>](compilers-element.md) element contains zero or more [\<compiler>](compiler-element.md) elements.</span></span> <span data-ttu-id="adc6a-129">Chaque [\<compiler>](compiler-element.md) élément spécifie les attributs de configuration du compilateur pour un fournisseur de langages spécifique.</span><span class="sxs-lookup"><span data-stu-id="adc6a-129">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="adc6a-130">Le .NET Framework définit les paramètres de compilateur initiaux dans le fichier de configuration de l’ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="adc6a-130">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="adc6a-131">Les développeurs et les éditeurs de compilateurs peuvent ajouter des paramètres de configuration pour une nouvelle implémentation <xref:System.CodeDom.Compiler.CodeDomProvider>.</span><span class="sxs-lookup"><span data-stu-id="adc6a-131">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="adc6a-132">Utilisez la méthode <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> pour énumérer par programmation les paramètres de configuration du compilateur et du fournisseur de langage sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="adc6a-132">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="adc6a-133">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="adc6a-133">Configuration File</span></span>  
 <span data-ttu-id="adc6a-134">Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur et dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="adc6a-134">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="adc6a-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="adc6a-135">Example</span></span>  
 <span data-ttu-id="adc6a-136">L’exemple suivant illustre une configuration de compilateur classique.</span><span class="sxs-lookup"><span data-stu-id="adc6a-136">The following example illustrates a typical compiler configuration.</span></span>  
  
```xml  
<configuration>  
  <system.codedom>  
    <compilers>  
      <!-- zero or more compiler elements -->  
      <compiler
        language="c#;cs;csharp"  
        extension=".cs"  
        type="Microsoft.CSharp.CSharpCodeProvider, System,
          Version=1.0.5000.0, Culture=neutral,
          PublicKeyToken=b77a5c561934e089"  
        compilerOptions=""  
        warningLevel="1" />  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="adc6a-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="adc6a-137">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="adc6a-138">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="adc6a-138">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="adc6a-139">Schéma des paramètres du fournisseur de langage et du compilateur</span><span class="sxs-lookup"><span data-stu-id="adc6a-139">Compiler and Language Provider Settings Schema</span></span>](index.md)
- [<span data-ttu-id="adc6a-140">\<compiler>Appartient</span><span class="sxs-lookup"><span data-stu-id="adc6a-140">\<compiler> Element</span></span>](compiler-element.md)
