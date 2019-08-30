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
ms.openlocfilehash: 5232c5bd2d4fad8104d156bfa86141ceb7f0dd93
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70167688"
---
# <a name="compilers-element"></a><span data-ttu-id="5b467-102">\<compilateurs > élément</span><span class="sxs-lookup"><span data-stu-id="5b467-102">\<compilers> Element</span></span>
<span data-ttu-id="5b467-103">Conteneur des éléments de configuration du compilateur ; contient zéro ou plusieurs éléments [\<compiler>](compiler-element.md).</span><span class="sxs-lookup"><span data-stu-id="5b467-103">Container for compiler configuration elements; contains zero or more [\<compiler>](compiler-element.md) elements.</span></span>  
  
[<span data-ttu-id="5b467-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="5b467-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="5b467-105">&nbsp;&nbsp;[ **\<System. CodeDom >** ](system-codedom-element.md)</span><span class="sxs-lookup"><span data-stu-id="5b467-105">&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)</span></span>  
<span data-ttu-id="5b467-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<compilateurs >**</span><span class="sxs-lookup"><span data-stu-id="5b467-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<compilers>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b467-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5b467-107">Syntax</span></span>  
  
```xml  
<compilers>  
  <compiler ... />  
</compilers>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5b467-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5b467-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5b467-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="5b467-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5b467-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="5b467-110">Attributes</span></span>  
 <span data-ttu-id="5b467-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="5b467-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5b467-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5b467-112">Child Elements</span></span>  
  
|<span data-ttu-id="5b467-113">Élément</span><span class="sxs-lookup"><span data-stu-id="5b467-113">Element</span></span>|<span data-ttu-id="5b467-114">Description</span><span class="sxs-lookup"><span data-stu-id="5b467-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5b467-115">\<compiler> Element</span><span class="sxs-lookup"><span data-stu-id="5b467-115">\<compiler> Element</span></span>](compiler-element.md)|<span data-ttu-id="5b467-116">Spécifie les attributs de configuration du compilateur pour un fournisseur de langage.</span><span class="sxs-lookup"><span data-stu-id="5b467-116">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5b467-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5b467-117">Parent Elements</span></span>  
  
|<span data-ttu-id="5b467-118">Élément</span><span class="sxs-lookup"><span data-stu-id="5b467-118">Element</span></span>|<span data-ttu-id="5b467-119">Description</span><span class="sxs-lookup"><span data-stu-id="5b467-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5b467-120">\<configuration>, élément</span><span class="sxs-lookup"><span data-stu-id="5b467-120">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="5b467-121">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5b467-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="5b467-122">\<System. CodeDom >, élément</span><span class="sxs-lookup"><span data-stu-id="5b467-122">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="5b467-123">Spécifie les paramètres de configuration du compilateur pour les fournisseurs de langages disponibles.</span><span class="sxs-lookup"><span data-stu-id="5b467-123">Specifies compiler configuration settings for available language providers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b467-124">Notes</span><span class="sxs-lookup"><span data-stu-id="5b467-124">Remarks</span></span>  
 <span data-ttu-id="5b467-125">L’élément compilers > contient les paramètres de configuration du compilateur pour les fournisseurs de langages sur un ordinateur. [ \<](compilers-element.md)</span><span class="sxs-lookup"><span data-stu-id="5b467-125">The [\<compilers>](compilers-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="5b467-126">Chaque élément de [> du compilateur spécifie les attributs de configuration du compilateur pour un fournisseur de langages spécifique. \<](compiler-element.md)</span><span class="sxs-lookup"><span data-stu-id="5b467-126">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="5b467-127">Le .NET Framework définit les paramètres initiaux du fournisseur de langage et du compilateur dans le fichier de configuration de l’ordinateur (machine. config).</span><span class="sxs-lookup"><span data-stu-id="5b467-127">The .NET Framework defines the initial compiler and language provider settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="5b467-128">Les développeurs et les éditeurs de compilateurs peuvent ajouter des paramètres de configuration pour une nouvelle implémentation <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5b467-128">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="5b467-129">Utilisez la méthode <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> pour énumérer par programmation les paramètres de configuration du compilateur et du fournisseur de langage sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="5b467-129">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="5b467-130">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="5b467-130">Configuration File</span></span>  
 <span data-ttu-id="5b467-131">Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur et dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="5b467-131">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b467-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="5b467-132">Example</span></span>  
 <span data-ttu-id="5b467-133">L’exemple suivant illustre un élément de configuration du compilateur classique.</span><span class="sxs-lookup"><span data-stu-id="5b467-133">The following example illustrates a typical compiler configuration element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5b467-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5b467-134">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="5b467-135">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="5b467-135">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="5b467-136">Schéma des paramètres du fournisseur de langage et du compilateur</span><span class="sxs-lookup"><span data-stu-id="5b467-136">Compiler and Language Provider Settings Schema</span></span>](index.md)
- [<span data-ttu-id="5b467-137">\<compiler> Element</span><span class="sxs-lookup"><span data-stu-id="5b467-137">\<compiler> Element</span></span>](compiler-element.md)
