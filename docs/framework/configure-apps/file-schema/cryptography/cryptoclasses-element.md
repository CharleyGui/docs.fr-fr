---
title: Élément <cryptoClasses>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClasses
helpviewer_keywords:
- <cryptoClasses> element
- cryptoClasses element
ms.assetid: 290d5f96-946d-4f02-babb-1d31ec0b8295
ms.openlocfilehash: 6601417f0b80f623b7698c4b072c35eca44343b7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732878"
---
# <a name="cryptoclasses-element"></a><span data-ttu-id="ec5cb-102">\<élément cryptoClasses ></span><span class="sxs-lookup"><span data-stu-id="ec5cb-102">\<cryptoClasses> Element</span></span>
<span data-ttu-id="ec5cb-103">Contient la liste des classes de chiffrement qui ont un mappage à un nom convivial dans l’élément [\<nameEntry>](nameentry-element.md).</span><span class="sxs-lookup"><span data-stu-id="ec5cb-103">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>  
  
[<span data-ttu-id="ec5cb-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="ec5cb-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="ec5cb-105">&nbsp;&nbsp;[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="ec5cb-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>  
<span data-ttu-id="ec5cb-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptographySettings** >](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="ec5cb-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)</span></span>  
<span data-ttu-id="ec5cb-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[ **cryptoNameMapping >** ](cryptonamemapping-element.md)</span><span class="sxs-lookup"><span data-stu-id="ec5cb-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)</span></span>  
<span data-ttu-id="ec5cb-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<cryptoClasses >**</span><span class="sxs-lookup"><span data-stu-id="ec5cb-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoClasses>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec5cb-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ec5cb-109">Syntax</span></span>  
  
```xml  
<cryptoClasses>   
</cryptoClasses>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ec5cb-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ec5cb-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ec5cb-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ec5cb-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ec5cb-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="ec5cb-112">Attributes</span></span>  
 <span data-ttu-id="ec5cb-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ec5cb-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ec5cb-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ec5cb-114">Child Elements</span></span>  
  
|<span data-ttu-id="ec5cb-115">Élément</span><span class="sxs-lookup"><span data-stu-id="ec5cb-115">Element</span></span>|<span data-ttu-id="ec5cb-116">Description</span><span class="sxs-lookup"><span data-stu-id="ec5cb-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ec5cb-117">\<cryptoClass></span><span class="sxs-lookup"><span data-stu-id="ec5cb-117">\<cryptoClass></span></span>](cryptoclass-element.md)|<span data-ttu-id="ec5cb-118">Contient une classe de chiffrement qui a un mappage à un nom convivial dans l’élément **\<nameEntry>** .</span><span class="sxs-lookup"><span data-stu-id="ec5cb-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ec5cb-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ec5cb-119">Parent Elements</span></span>  
  
|<span data-ttu-id="ec5cb-120">Élément</span><span class="sxs-lookup"><span data-stu-id="ec5cb-120">Element</span></span>|<span data-ttu-id="ec5cb-121">Description</span><span class="sxs-lookup"><span data-stu-id="ec5cb-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ec5cb-122">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ec5cb-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="ec5cb-123">Contient des paramètres de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="ec5cb-123">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="ec5cb-124">Contient des mappages de classes à des noms conviviaux.</span><span class="sxs-lookup"><span data-stu-id="ec5cb-124">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="ec5cb-125">Contient l’élément `cryptographySettings`.</span><span class="sxs-lookup"><span data-stu-id="ec5cb-125">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ec5cb-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="ec5cb-126">Example</span></span>  
 <span data-ttu-id="ec5cb-127">L’exemple suivant montre comment utiliser l’élément **\<cryptoClass >** pour faire référence à une classe de chiffrement et configurer le Runtime.</span><span class="sxs-lookup"><span data-stu-id="ec5cb-127">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="ec5cb-128">Vous pouvez ensuite passer la chaîne « RSA » à la méthode <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> et utiliser la méthode <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> pour retourner un objet `MyCryptoRSAClass`.</span><span class="sxs-lookup"><span data-stu-id="ec5cb-128">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
               <!-- Other cryptography classes go here. -->  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
             <!-- Mappings to other cryptography classes go here. -->  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ec5cb-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ec5cb-129">See also</span></span>

- <xref:System.Security.Cryptography>
- [<span data-ttu-id="ec5cb-130">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="ec5cb-130">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="ec5cb-131">Schéma des paramètres de chiffrement</span><span class="sxs-lookup"><span data-stu-id="ec5cb-131">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ec5cb-132">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="ec5cb-132">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="ec5cb-133">System.Security.Cryptography.CryptoConfig.CreateFromName</span><span class="sxs-lookup"><span data-stu-id="ec5cb-133">System.Security.Cryptography.CryptoConfig.CreateFromName</span></span>](xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A)
- [<span data-ttu-id="ec5cb-134">Configuration des classes de chiffrement</span><span class="sxs-lookup"><span data-stu-id="ec5cb-134">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
