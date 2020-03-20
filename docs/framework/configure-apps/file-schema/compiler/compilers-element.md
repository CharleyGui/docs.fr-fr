---
title: Élément <compilers>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compilers
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers
helpviewer_keywords:
- compiler configuration elements, <compilers> element
- <compilers> element
- compilers element
ms.assetid: d40fba59-98f9-4783-ae0c-2ebea27ce77b
ms.openlocfilehash: 09b1efe321c39402c9280eda0e9def9112462470
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155412"
---
# <a name="compilers-element"></a><span data-ttu-id="95d0c-102">\<compilateurs> Element</span><span class="sxs-lookup"><span data-stu-id="95d0c-102">\<compilers> Element</span></span>
<span data-ttu-id="95d0c-103">Conteneur pour éléments de configuration de compilateur; contient zéro ou plus [ \<compilateur>](compiler-element.md) éléments.</span><span class="sxs-lookup"><span data-stu-id="95d0c-103">Container for compiler configuration elements; contains zero or more [\<compiler>](compiler-element.md) elements.</span></span>  

<span data-ttu-id="95d0c-104">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="95d0c-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="95d0c-105">&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)</span><span class="sxs-lookup"><span data-stu-id="95d0c-105">&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)</span></span>\
<span data-ttu-id="95d0c-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<compilateurs>**</span><span class="sxs-lookup"><span data-stu-id="95d0c-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<compilers>**</span></span>

## <a name="syntax"></a><span data-ttu-id="95d0c-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95d0c-107">Syntax</span></span>  
  
```xml  
<compilers>  
  <compiler ... />  
</compilers>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="95d0c-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="95d0c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="95d0c-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="95d0c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="95d0c-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="95d0c-110">Attributes</span></span>  
 <span data-ttu-id="95d0c-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="95d0c-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="95d0c-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="95d0c-112">Child Elements</span></span>  
  
|<span data-ttu-id="95d0c-113">Élément</span><span class="sxs-lookup"><span data-stu-id="95d0c-113">Element</span></span>|<span data-ttu-id="95d0c-114">Description</span><span class="sxs-lookup"><span data-stu-id="95d0c-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="95d0c-115">\<compilateur> Element</span><span class="sxs-lookup"><span data-stu-id="95d0c-115">\<compiler> Element</span></span>](compiler-element.md)|<span data-ttu-id="95d0c-116">Spécifie les attributs de configuration du compilateur pour un fournisseur de langage.</span><span class="sxs-lookup"><span data-stu-id="95d0c-116">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="95d0c-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="95d0c-117">Parent Elements</span></span>  
  
|<span data-ttu-id="95d0c-118">Élément</span><span class="sxs-lookup"><span data-stu-id="95d0c-118">Element</span></span>|<span data-ttu-id="95d0c-119">Description</span><span class="sxs-lookup"><span data-stu-id="95d0c-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="95d0c-120">\<configuration> Element</span><span class="sxs-lookup"><span data-stu-id="95d0c-120">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="95d0c-121">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="95d0c-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="95d0c-122">\<system.codedom> Element</span><span class="sxs-lookup"><span data-stu-id="95d0c-122">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="95d0c-123">Spécifie les paramètres de configuration du compilateur pour les fournisseurs de langages disponibles.</span><span class="sxs-lookup"><span data-stu-id="95d0c-123">Specifies compiler configuration settings for available language providers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95d0c-124">Notes </span><span class="sxs-lookup"><span data-stu-id="95d0c-124">Remarks</span></span>  
 <span data-ttu-id="95d0c-125">Les [ \<compilateurs>'élément](compilers-element.md) contient les paramètres de configuration du compilateur pour les fournisseurs de langues sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="95d0c-125">The [\<compilers>](compilers-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="95d0c-126">Chaque [ \<compilateur>](compiler-element.md) élément spécifie les attributs de configuration du compilateur pour un fournisseur de langue spécifique.</span><span class="sxs-lookup"><span data-stu-id="95d0c-126">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="95d0c-127">Le cadre .NET définit les paramètres initiaux du compilateur et du fournisseur de langues dans le fichier de configuration de la machine (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="95d0c-127">The .NET Framework defines the initial compiler and language provider settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="95d0c-128">Les développeurs et les éditeurs de compilateurs peuvent ajouter des paramètres de configuration pour une nouvelle implémentation <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="95d0c-128">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="95d0c-129">Utilisez la méthode <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> pour énumérer par programmation les paramètres de configuration du compilateur et du fournisseur de langage sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="95d0c-129">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="95d0c-130">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="95d0c-130">Configuration File</span></span>  
 <span data-ttu-id="95d0c-131">Cet élément peut être utilisé dans le fichier de configuration de la machine et le fichier de configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="95d0c-131">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95d0c-132"> Exemple</span><span class="sxs-lookup"><span data-stu-id="95d0c-132">Example</span></span>  
 <span data-ttu-id="95d0c-133">L’exemple suivant illustre un élément de configuration du compilateur classique.</span><span class="sxs-lookup"><span data-stu-id="95d0c-133">The following example illustrates a typical compiler configuration element.</span></span>  
  
```xml  
<configuration>  
   <system.codedom>  
     <compilers>  
       <!-- zero or more compiler elements -->  
       <compiler
          language="c#;cs;csharp"
          extension=".cs"  
          type="Microsoft.CSharp.CSharpCodeProvider, System, Version=1.0.5000.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
          compilerOptions=""
          warningLevel="1" />  
     </compilers>  
   </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="95d0c-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="95d0c-134">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="95d0c-135">Configuration Fichier Schema</span><span class="sxs-lookup"><span data-stu-id="95d0c-135">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="95d0c-136">Compilateur et Paramètres de fournisseur de langues Schema</span><span class="sxs-lookup"><span data-stu-id="95d0c-136">Compiler and Language Provider Settings Schema</span></span>](index.md)
- [<span data-ttu-id="95d0c-137">\<compilateur> Element</span><span class="sxs-lookup"><span data-stu-id="95d0c-137">\<compiler> Element</span></span>](compiler-element.md)
