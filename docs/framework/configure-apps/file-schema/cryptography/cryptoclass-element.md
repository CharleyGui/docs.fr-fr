---
title: Élément <cryptoClass>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses/cryptoClass
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClass
helpviewer_keywords:
- cryptoClass element
- <cryptoClass> element
ms.assetid: 03db52ef-010e-44ea-b6fd-b9c900ecad50
ms.openlocfilehash: 4872fbd6fa043902e8c69f158bee5d0c915ec83a
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088660"
---
# <a name="cryptoclass-element"></a><span data-ttu-id="c22c6-102">\<élément cryptoClass ></span><span class="sxs-lookup"><span data-stu-id="c22c6-102">\<cryptoClass> Element</span></span>
<span data-ttu-id="c22c6-103">Contient une classe de chiffrement qui a un mappage à un nom convivial dans l’élément [\<nameEntry>](nameentry-element.md).</span><span class="sxs-lookup"><span data-stu-id="c22c6-103">Contains a cryptography class that has a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>  

<span data-ttu-id="c22c6-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c22c6-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c22c6-105">&nbsp;&nbsp;[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="c22c6-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>\
<span data-ttu-id="c22c6-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptographySettings**](cryptographysettings-element.md) ></span><span class="sxs-lookup"><span data-stu-id="c22c6-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)</span></span>\
<span data-ttu-id="c22c6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**cryptoNameMapping**](cryptonamemapping-element.md) ></span><span class="sxs-lookup"><span data-stu-id="c22c6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)</span></span>\
<span data-ttu-id="c22c6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptoClasses**](cryptoclasses-element.md) ></span><span class="sxs-lookup"><span data-stu-id="c22c6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClasses>**](cryptoclasses-element.md)</span></span>\
<span data-ttu-id="c22c6-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**cryptoClass >**</span><span class="sxs-lookup"><span data-stu-id="c22c6-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoClass>**</span></span>

## <a name="syntax"></a><span data-ttu-id="c22c6-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c22c6-110">Syntax</span></span>  
  
```xml  
<cryptoClass customClassName="fully qualified type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c22c6-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c22c6-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c22c6-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="c22c6-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c22c6-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="c22c6-113">Attributes</span></span>  
  
|<span data-ttu-id="c22c6-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="c22c6-114">Attribute</span></span>|<span data-ttu-id="c22c6-115">Description</span><span class="sxs-lookup"><span data-stu-id="c22c6-115">Description</span></span>|  
|---------------|-----------------|  
|`customClassName`|<span data-ttu-id="c22c6-116">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="c22c6-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="c22c6-117">Contient les informations relatives à la classe de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="c22c6-117">Contains the information for the cryptography class.</span></span> <span data-ttu-id="c22c6-118">Utilisez cet attribut pour fournir un nom abrégé pour votre classe.</span><span class="sxs-lookup"><span data-stu-id="c22c6-118">Use this attribute to provide a short name for your class.</span></span> <span data-ttu-id="c22c6-119">Vous devez spécifier une chaîne qui répond aux exigences spécifiées dans [spécification de noms de types qualifiés complets](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="c22c6-119">You must specify a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c22c6-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c22c6-120">Child Elements</span></span>  
 <span data-ttu-id="c22c6-121">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="c22c6-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c22c6-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c22c6-122">Parent Elements</span></span>  
  
|<span data-ttu-id="c22c6-123">Élément</span><span class="sxs-lookup"><span data-stu-id="c22c6-123">Element</span></span>|<span data-ttu-id="c22c6-124">Description</span><span class="sxs-lookup"><span data-stu-id="c22c6-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c22c6-125">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c22c6-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptoClasses`|<span data-ttu-id="c22c6-126">Contient la liste des classes de chiffrement qui ont un mappage à un nom convivial dans l’élément [\<nameEntry>](nameentry-element.md).</span><span class="sxs-lookup"><span data-stu-id="c22c6-126">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="c22c6-127">Contient des paramètres de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="c22c6-127">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="c22c6-128">Contient des mappages de classes à des noms conviviaux.</span><span class="sxs-lookup"><span data-stu-id="c22c6-128">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="c22c6-129">Contient l’élément [\<cryptographySettings>](cryptographysettings-element.md).</span><span class="sxs-lookup"><span data-stu-id="c22c6-129">Contains the [\<cryptographySettings>](cryptographysettings-element.md) element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c22c6-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="c22c6-130">Example</span></span>  
 <span data-ttu-id="c22c6-131">L’exemple suivant montre comment utiliser l’élément **\<cryptoClass >** pour faire référence à une classe de chiffrement et configurer le Runtime.</span><span class="sxs-lookup"><span data-stu-id="c22c6-131">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="c22c6-132">Vous pouvez ensuite passer la chaîne « RSA » à la méthode <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> et utiliser la méthode <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> pour retourner un objet `MyCryptoRSAClass`.</span><span class="sxs-lookup"><span data-stu-id="c22c6-132">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c22c6-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c22c6-133">See also</span></span>

- [<span data-ttu-id="c22c6-134">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="c22c6-134">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="c22c6-135">Schéma des paramètres de chiffrement</span><span class="sxs-lookup"><span data-stu-id="c22c6-135">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c22c6-136">Services de chiffrement</span><span class="sxs-lookup"><span data-stu-id="c22c6-136">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="c22c6-137">Configuration des classes de chiffrement</span><span class="sxs-lookup"><span data-stu-id="c22c6-137">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
