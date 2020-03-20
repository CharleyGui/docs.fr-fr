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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155386"
---
# <a name="systemcodedom-element"></a><span data-ttu-id="9409b-102">\<system.codedom> Element</span><span class="sxs-lookup"><span data-stu-id="9409b-102">\<system.codedom> Element</span></span>
<span data-ttu-id="9409b-103">Spécifie les paramètres de configuration du compilateur pour les fournisseurs de langages disponibles.</span><span class="sxs-lookup"><span data-stu-id="9409b-103">Specifies compiler configuration settings for available language providers.</span></span>  
  
[<span data-ttu-id="9409b-104">**\<configuration>**</span><span class="sxs-lookup"><span data-stu-id="9409b-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="9409b-105">&nbsp;&nbsp;**\<system.codedom>**</span><span class="sxs-lookup"><span data-stu-id="9409b-105">&nbsp;&nbsp;**\<system.codedom>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9409b-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9409b-106">Syntax</span></span>  
  
```xml  
<system.codedom>  
  <compilers> ... </compilers>  
</system.codedom>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9409b-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="9409b-107">Attributes and Elements</span></span>  
 <span data-ttu-id="9409b-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="9409b-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9409b-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="9409b-109">Attributes</span></span>  
 <span data-ttu-id="9409b-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="9409b-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9409b-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9409b-111">Child Elements</span></span>  
  
|<span data-ttu-id="9409b-112">Élément</span><span class="sxs-lookup"><span data-stu-id="9409b-112">Element</span></span>|<span data-ttu-id="9409b-113">Description</span><span class="sxs-lookup"><span data-stu-id="9409b-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9409b-114">\<compilateurs></span><span class="sxs-lookup"><span data-stu-id="9409b-114">\<compilers></span></span>](compilers-element.md)|<span data-ttu-id="9409b-115">Conteneur pour éléments de configuration de compilateur; contient zéro ou plus [ \<compilateur>](compiler-element.md) éléments.</span><span class="sxs-lookup"><span data-stu-id="9409b-115">Container for compiler configuration elements; contains zero or more [\<compiler>](compiler-element.md) elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9409b-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9409b-116">Parent Elements</span></span>  
  
|<span data-ttu-id="9409b-117">Élément</span><span class="sxs-lookup"><span data-stu-id="9409b-117">Element</span></span>|<span data-ttu-id="9409b-118">Description</span><span class="sxs-lookup"><span data-stu-id="9409b-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9409b-119">\<configuration></span><span class="sxs-lookup"><span data-stu-id="9409b-119">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="9409b-120">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9409b-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9409b-121">Notes </span><span class="sxs-lookup"><span data-stu-id="9409b-121">Remarks</span></span>  
  
## <a name="net-framework-version-20"></a><span data-ttu-id="9409b-122">.NET Version-cadre 2.0</span><span class="sxs-lookup"><span data-stu-id="9409b-122">.NET Framework Version 2.0</span></span>  
 <span data-ttu-id="9409b-123">[ \<L’élément system.codedom>](system-codedom-element.md) contient des paramètres de configuration compilateur pour les fournisseurs de langues installés sur un <xref:Microsoft.CSharp.CSharpCodeProvider> ordinateur <xref:Microsoft.VisualBasic.VBCodeProvider>en plus des fournisseurs par défaut qui sont installés avec le cadre .NET, tels que le et le .</span><span class="sxs-lookup"><span data-stu-id="9409b-123">The [\<system.codedom>](system-codedom-element.md) element contains compiler configuration settings for language providers installed on a computer in addition to the default providers that are installed with the .NET Framework, such as the <xref:Microsoft.CSharp.CSharpCodeProvider> and the <xref:Microsoft.VisualBasic.VBCodeProvider>.</span></span> <span data-ttu-id="9409b-124">Les [ \<compilateurs>](compilers-element.md) élément contient zéro ou plus [ \<compilateur>](compiler-element.md) éléments.</span><span class="sxs-lookup"><span data-stu-id="9409b-124">The [\<compilers>](compilers-element.md) element contains zero or more [\<compiler>](compiler-element.md) elements.</span></span> <span data-ttu-id="9409b-125">Chaque [ \<compilateur>](compiler-element.md) élément spécifie les attributs de configuration du compilateur pour un fournisseur de langue spécifique.</span><span class="sxs-lookup"><span data-stu-id="9409b-125">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="9409b-126">Les développeurs et les fournisseurs de compilateur peuvent ajouter des paramètres <xref:System.CodeDom.Compiler.CodeDomProvider> de configuration au fichier de configuration de la machine (Machine.config) pour une nouvelle implémentation.</span><span class="sxs-lookup"><span data-stu-id="9409b-126">Developers and compiler vendors can add configuration settings to the machine configuration file (Machine.config) for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="9409b-127">Utilisez <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> la méthode pour énumérer programmatiquement les fournisseurs de langues par défaut et les fournisseurs de langues identifiés par les paramètres de configuration du compilateur sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="9409b-127">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate both the default language providers and language providers identified by the compiler configuration settings on a computer.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9409b-128">Dans les versions cadre .NET 1.0 et 1.1, les fournisseurs de langue par défaut fournis par le cadre .NET sont identifiés dans les [ \<compilateurs>](compilers-element.md) élément.</span><span class="sxs-lookup"><span data-stu-id="9409b-128">In the .NET Framework versions 1.0 and 1.1, the default language providers supplied by the .NET Framework are identified in the [\<compilers>](compilers-element.md) element.</span></span> <span data-ttu-id="9409b-129">Dans la version cadre .NET 2.0, les fournisseurs de langage par défaut ne sont pas identifiés <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> dans les [ \<compilateurs>](compilers-element.md) élément, mais peuvent être énumérés à l’aide de la méthode.</span><span class="sxs-lookup"><span data-stu-id="9409b-129">In the .NET Framework version 2.0, the default language providers are not identified in the [\<compilers>](compilers-element.md) element, but can be enumerated using the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> method.</span></span>  
  
## <a name="net-framework-versions-10-and-11"></a><span data-ttu-id="9409b-130">.NET Versions-cadre 1.0 et 1.1</span><span class="sxs-lookup"><span data-stu-id="9409b-130">.NET Framework Versions 1.0 and 1.1</span></span>  
 <span data-ttu-id="9409b-131">[ \<L’élément system.codedom>](system-codedom-element.md) contient les paramètres de configuration du compilateur pour les fournisseurs de langues sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="9409b-131">The [\<system.codedom>](system-codedom-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="9409b-132">Les [ \<compilateurs>](compilers-element.md) élément contient zéro ou plus [ \<compilateur>](compiler-element.md) éléments.</span><span class="sxs-lookup"><span data-stu-id="9409b-132">The [\<compilers>](compilers-element.md) element contains zero or more [\<compiler>](compiler-element.md) elements.</span></span> <span data-ttu-id="9409b-133">Chaque [ \<compilateur>](compiler-element.md) élément spécifie les attributs de configuration du compilateur pour un fournisseur de langue spécifique.</span><span class="sxs-lookup"><span data-stu-id="9409b-133">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="9409b-134">Le .NET Framework définit les paramètres de compilateur initiaux dans le fichier de configuration de l’ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="9409b-134">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="9409b-135">Les développeurs et les éditeurs de compilateurs peuvent ajouter des paramètres de configuration pour une nouvelle implémentation <xref:System.CodeDom.Compiler.CodeDomProvider>.</span><span class="sxs-lookup"><span data-stu-id="9409b-135">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="9409b-136">Utilisez la méthode <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> pour énumérer par programmation les paramètres de configuration du compilateur et du fournisseur de langage sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="9409b-136">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="9409b-137">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="9409b-137">Configuration File</span></span>  
 <span data-ttu-id="9409b-138">Cet élément peut être utilisé dans le fichier de configuration de la machine et le fichier de configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="9409b-138">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9409b-139"> Exemple</span><span class="sxs-lookup"><span data-stu-id="9409b-139">Example</span></span>  
 <span data-ttu-id="9409b-140">L’exemple suivant illustre une configuration compilateur typique.</span><span class="sxs-lookup"><span data-stu-id="9409b-140">The following example illustrates a typical compiler configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9409b-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9409b-141">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="9409b-142">Configuration Fichier Schema</span><span class="sxs-lookup"><span data-stu-id="9409b-142">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="9409b-143">Compilateur et Paramètres de fournisseur de langues Schema</span><span class="sxs-lookup"><span data-stu-id="9409b-143">Compiler and Language Provider Settings Schema</span></span>](index.md)
- [<span data-ttu-id="9409b-144">\<compilateur> Element</span><span class="sxs-lookup"><span data-stu-id="9409b-144">\<compiler> Element</span></span>](compiler-element.md)
